//procedurally generated terrain with roads.

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class CityGenerator : MonoBehaviour
{

    public GameObject[] buildings;
    public GameObject xstreets;
    public GameObject zstreets;
    public GameObject crossroad;
    public int mapWidth = 30;
    public int mapHeight = 30;
    int[,] mapgrid;
    int buildingFootprint = 25; //formula to set footprint to actual (w,h) of object being placed?

    // Use this for initialization
    void Start()
    {

        mapgrid = new int[mapWidth, mapHeight];

        //generate map data
        float seed = Random.Range(0, 100);
        for (int h = 0; h < mapHeight; h++)
        {
            for (int w = 0; w < mapWidth; w++)
            {
                mapgrid[w, h] = (int)(Mathf.PerlinNoise(w/10.0f + seed, h/10.0f + seed) * 200);
            }
        }

        //build streets
        int x = 0;
        for (int n = 0; n < 50; n++)
        {
            for (int h = 0; h < mapHeight; h++)
            {
                mapgrid[x, h] = -1;
            }
            x += Random.Range(3,5);
            if (x >= mapWidth) break;
            }

        int z = 0;
        for(int n = 0; n < 10; n++)
        {
            for(int w = 0; w < mapWidth; w++)
            {
                Debug.Log(z);
                if (mapgrid[w, z] == -1) //put in crossroad
                    mapgrid[w, z] = -3;
                else
                    mapgrid[w, z] = -2;
            }
            z += Random.Range(3, 5);
            if (z >= mapHeight) break;
        }

        //generate city
        for (int h = 0; h < mapHeight; h++)
        {
            for (int w = 0; w < mapWidth; w++)
            {
                int result = mapgrid[w, h];
                Vector3 pos = new Vector3(w * buildingFootprint, 0, h * buildingFootprint); //formula to detect terrain height and set each object Y to terrain height - 0.5
                if (result < -2)
                    Instantiate(crossroad, pos, crossroad.transform.rotation);
                else if (result < -1)
                    Instantiate(xstreets, pos, xstreets.transform.rotation);
                else if (result < 0)
                    Instantiate(zstreets, pos, zstreets.transform.rotation);
                else if (result < 1)
                    Instantiate(buildings[0], pos, Quaternion.identity); //formula to rotate random degrees around Y?
                else if (result < 2)
                    Instantiate(buildings[1], pos, Quaternion.identity);
                else if (result < 3)
                    Instantiate(buildings[2], pos, Quaternion.identity);
                else if (result < 8)
                    Instantiate(buildings[3], pos, Quaternion.identity);
                else if (result < 9)
                    Instantiate(buildings[4], pos, Quaternion.identity);
                else if (result < 12)
                    Instantiate(buildings[5], pos, Quaternion.identity);
                else if (result < 15)
                    Instantiate(buildings[6], pos, Quaternion.identity);
                else if (result < 18)
                    Instantiate(buildings[7], pos, Quaternion.identity);
                else if (result < 21)
                    Instantiate(buildings[8], pos, Quaternion.identity);
                else if (result < 24)
                    Instantiate(buildings[9], pos, Quaternion.identity);
                else if (result < 27)
                    Instantiate(buildings[10], pos, Quaternion.identity);
                else if (result < 30)
                    Instantiate(buildings[11], pos, Quaternion.identity);
                else if (result < 33)
                    Instantiate(buildings[12], pos, Quaternion.identity);
                else if (result < 36)
                    Instantiate(buildings[13], pos, Quaternion.identity);
                else if (result < 39)
                    Instantiate(buildings[14], pos, Quaternion.identity);
                else if (result < 42)
                    Instantiate(buildings[15], pos, Quaternion.identity);
                else if (result < 45)
                    Instantiate(buildings[16], pos, Quaternion.identity);
                else if (result < 48)
                    Instantiate(buildings[17], pos, Quaternion.identity);
                else if (result < 51)
                    Instantiate(buildings[18], pos, Quaternion.identity);
                else if (result < 54)
                    Instantiate(buildings[19], pos, Quaternion.identity);
                else if (result < 57)
                    Instantiate(buildings[20], pos, Quaternion.identity);
                else if (result < 60)
                    Instantiate(buildings[21], pos, Quaternion.identity);
                else if (result < 63)
                    Instantiate(buildings[22], pos, Quaternion.identity);
                else if (result < 66)
                    Instantiate(buildings[23], pos, Quaternion.identity);
                else if (result < 69)
                    Instantiate(buildings[24], pos, Quaternion.identity);
                else if (result < 72)
                    Instantiate(buildings[25], pos, Quaternion.identity);
                else if (result < 75)
                    Instantiate(buildings[26], pos, Quaternion.identity);
                else if (result < 78)
                    Instantiate(buildings[27], pos, Quaternion.identity);
                else if (result < 81)
                    Instantiate(buildings[28], pos, Quaternion.identity);
                else if (result < 84)
                    Instantiate(buildings[29], pos, Quaternion.identity);
                else if (result < 87)
                    Instantiate(buildings[30], pos, Quaternion.identity);
                else if (result < 89)
                    Instantiate(buildings[31], pos, Quaternion.identity);
                else if (result < 90)
                    Instantiate(buildings[32], pos, Quaternion.identity);
                else if (result < 91)
                    Instantiate(buildings[33], pos, Quaternion.identity);
                else if (result < 92)
                    Instantiate(buildings[34], pos, Quaternion.identity);
                else if (result < 93)
                    Instantiate(buildings[35], pos, Quaternion.identity);
                else if (result < 94)
                    Instantiate(buildings[36], pos, Quaternion.identity);
                else if (result < 95)
                    Instantiate(buildings[37], pos, Quaternion.identity);
                else if (result < 96)
                    Instantiate(buildings[38], pos, Quaternion.identity);
                else if (result < 97)
                    Instantiate(buildings[39], pos, Quaternion.identity);
                else if (result < 98)
                    Instantiate(buildings[40], pos, Quaternion.identity);
                else if (result < 99)
                    Instantiate(buildings[41], pos, Quaternion.identity);
                else if (result < 200)
                        Instantiate(buildings[42], pos, Quaternion.identity);
            }
        }
    }

        // Update is called once per frame
        void Update()
        {

        }
    }



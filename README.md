using System.Collections;
using System.Collections.Generic;
using System.Diagnostics.CodeAnalysis;
using UnityEditor.VersionControl;
using UnityEngine;

public class ObjectGenerator : MonoBehaviour
{
    public GameObject GeneratedLocations;
    public GameObject RoomObjects;

    void CreateObject(GameObject objectToClone, GameObject locationObject)
    {

      
        GameObject Clone = Instantiate(objectToClone, locationObject.transform.position, Quaternion.identity);
        Clone.SetActive(true);
    }

    void Start()
    {
        foreach (Transform location in GeneratedLocations.transform)
        {
            int randomNumber = Random.Range(0, RoomObjects.transform.childCount);
            CreateObject(RoomObjects.transform.GetChild(randomNumber).gameObject, location.gameObject);
        }
    }
}

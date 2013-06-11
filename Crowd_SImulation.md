Summer
======

Crowd Simulation of Cubes/Unity 3D

======






using UnityEngine;
using System.Collections;

public class CubeMovement : MonoBehaviour {

  // Use this for initialization
	void Start () {
		target =  new Vector3 (positionX(), 2, positionZ());
		transform.position = new Vector3(startX(), 9.0f, startZ());
		
		character = GetComponent<CharacterController>();
	}
	
	private Vector3 startPoint;
	private Vector3 endPoint;
	private float startTime;
	private Vector3 target;
	
	//Prevents Collision?
	CharacterController character;
	
	//Randomized Starting Position X-Axis
	private float startX () {
		float x = Random.Range (1,300);
		return x;
		
	}
	
	private float startY () {
		float y = Random.Range (1,100);
		return y;
		
	}

	//Randomized Starting Position Z-Axis
	private float startZ () {
		float z = Random.Range (1,300);	
		return z;
	}
	
	//Target Position X-Axis
	private float positionX () {
		float x = Random.Range (100, 2000);
		return x;
	}
	
	//Target Position Z-Axis
	private float positionZ () {
		float z = Random.Range (100, 2000);
		return z;
	}
	//The wait time before the change
	IEnumerator MyDelayMethod(float delay)
	{
    	
   		 yield return new WaitForSeconds(delay); 
	}
	
	//For the camera
	
	public Camera cam1;
	public Camera cam2;
	public Camera cam3;
	public Camera cam4;
	public Camera cam5;
	public Camera cam6;

	void ChangeCamera() {
		
		
		if (Input.GetKeyDown(KeyCode.Alpha1))
		{
			Camera.main.enabled = true;
			cam1.enabled = false;
			cam2.enabled = false;
			cam3.enabled = false;
			cam4.enabled = false;
			cam5.enabled = false;
			cam6.enabled = false;
		}
		else if (Input.GetKeyDown(KeyCode.Alpha2))
		{
			cam1.enabled = true;
			cam2.enabled = false;
			cam3.enabled = false;
			cam4.enabled = false;
			cam5.enabled = false;
			cam6.enabled = false;
		}
		else if (Input.GetKeyDown (KeyCode.Alpha3))
		{
			cam1.enabled = false;
			cam2.enabled = true;
			cam3.enabled = false;
			cam4.enabled = false;
			cam5.enabled = false;
			cam6.enabled = false;
		}
		else if (Input.GetKeyDown (KeyCode.Alpha4))
		{
			cam1.enabled = false;
			cam2.enabled = false;
			cam3.enabled = true;
			cam4.enabled = false;
			cam5.enabled = false;
			cam6.enabled = false;
		}
		else if (Input.GetKeyDown (KeyCode.Alpha5))
		{
			cam1.enabled = false;
			cam2.enabled = false;
			cam3.enabled = false;
			cam4.enabled = true;
			cam5.enabled = false;
			cam6.enabled = false;
		}
		else if (Input.GetKeyDown (KeyCode.Alpha6))
		{
			cam1.enabled = false;
			cam2.enabled = false;
			cam3.enabled = false;
			cam4.enabled = false;
			cam5.enabled = true;
			cam6.enabled = false;
		}
		else if (Input.GetKeyDown (KeyCode.Alpha7))
		{
			cam1.enabled = false;
			cam2.enabled = false;
			cam3.enabled = false;
			cam4.enabled = false;
			cam5.enabled = false;
			cam6.enabled = true;
		}	
	} 
	
	
	// Update is called once per frame
	void Update () {
		//Find a way for USER to choose the amount of objects on screen
		ChangeCamera();
		transform.position = Vector3.MoveTowards(transform.position, target, 80*Time.deltaTime);
		Vector3 distance = (transform.position - target);
			
		//Magnitude Example: Vector = (1, 1, 1) Magnitude = SQUARE ROOT (1(squared) + 1(squared) + 1(squared))
		//This causes the target position as soon as the object gets close to its position
		if (distance.magnitude < 1)
		{
			target = new Vector3 (positionX () , 2, positionZ ());
		}
		
	}
	
}

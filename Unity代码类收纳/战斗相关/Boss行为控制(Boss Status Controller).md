# Boss行为控制(Boss Status Controller)

用于控制Boss移动和不同阶段的攻击等。

## 利用Animator控制Boss状态 作者：Brackeys  
  
<p align="center">  
    
  <img src="https://user-images.githubusercontent.com/28853235/210261414-e68e4973-bb45-475b-a29a-6f5935a22b6a.png" />    
 <p align="center">  
         <sup>  （图片来源：见原视频链接）</sup>  
<p align="center">   
   用trigger触发攻击动画，攻击动画结束后回到移动/静止（Intro为入场动画）
   

  
  
  ## 
  
在RUN动画上加入脚本<sup>（点击动画方块然后Add Behavior  ）</sup> 
```
public class Boss_Run : StateMachineBehaviour
{

  //设置变量


    override public void OnStateEnter(Animator animator, AnimatorStateInfo stateInfo, int layerIndex)
    {
      
		  //Boss开始移动  
		  //在此获取启动时需要的组件，使用方法类似于void Start  

	}


	override public void OnStateUpdate(Animator animator, AnimatorStateInfo stateInfo, int layerIndex)
	{
		
		  //每帧执行（此案例中为移动时每帧执行）
		  //在Brackeys的源代码中，此处用于跟随玩家位置，即Boss会向玩家的方位移动，需要在OnStateEnter获取player transform
      
		  //在Brackeys的源代码中，此处有一个范围判定： 
		if (Vector2.Distance(player.position, rb.position) <= attackRange)
		{
                                                                       
		  //玩家在攻击范围内时发动攻击                 
			animator.SetTrigger("Attack");
                                                                       
		}
                                                                       
	}


	override public void OnStateExit(Animator animator, AnimatorStateInfo stateInfo, int layerIndex)
	{
                                                                       
		  //移动动画结束
		  //像此案例中，Boss只有移动和攻击两种状态，可以在此处trigger attack的动画                                                          
                                                                       
	}
} 
```  
## 在动画中央加入攻击判定 作者：Brackeys  

 ![image](https://user-images.githubusercontent.com/28853235/210264072-a74f33fc-8762-47a9-aef8-06089a14e44d.png)
   <p align="center">  
                                                                      <sup>  （图片来源：见原视频链接）</sup>   
     <p align="center"> 
在时间轴上选择武器接触到玩家的那一帧，选择add event（见鼠标处）便可以触发带判定和伤害的脚本  
       
以这种方式判定可以避免写hitbox的移动，然而详细情况还取决于你的游戏。  
关于hitbox/hurtbox的移动，可参考本篇文章中的图片：  
[【英文文章】格斗游戏中的hitbox和hurtbox](https://strangewire.blogspot.com/2018/05/hitboxes-and-hurtboxes-in-unity.html?m=1)   
  ## 
         
[源代码链接（Github）](https://github.com/Brackeys/Boss-Battle)  
[源视频链接（Youtube）](https://www.youtube.com/watch?v=AD4JIXQDw0s&ab_channel=Brackeys)                                                     

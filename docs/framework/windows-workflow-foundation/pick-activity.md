---
title: Vyberte aktivitu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a76b666dde6674740790c161753570193912afd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="pick-activity"></a>Vyberte aktivitu
<xref:System.Activities.Statements.Pick> Aktivity zjednodušuje modelování sady aktivačních událostí a jejich odpovídající obslužné rutiny.  A <xref:System.Activities.Statements.Pick> aktivity obsahuje kolekci <xref:System.Activities.Statements.PickBranch> aktivity, kde každý <xref:System.Activities.Statements.PickBranch> je párování mezi <xref:System.Activities.Statements.PickBranch.Trigger%2A> aktivity a <xref:System.Activities.Statements.PickBranch.Action%2A> aktivity.  V době provedení aktivačních událostí pro všechny větve provedení paralelně.  Po dokončení jedna aktivační událost, pak je jeho odpovídající akci provést, a všechny ostatní aktivační události došlo ke zrušení.  Chování [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> aktivity je podobná [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> aktivity.  
  
 Následující snímek obrazovky [pomocí aktivity vyberte](../../../docs/framework/windows-workflow-foundation/samples/using-the-pick-activity.md) SDK – ukázka zobrazuje vybrat aktivitu se dvě větve.  Jeden větve je aktivační událost volá **vstup pro čtení**, vlastní aktivity, který čte vstupní z příkazového řádku. Má druhé větve <xref:System.Activities.Statements.Delay> aktivity aktivační události. Pokud **vstup pro čtení** aktivita přijímá data před <xref:System.Activities.Statements.Delay> dokončení aktivity <xref:System.Activities.Statements.Delay> zpoždění, budou zrušeny a pohlednice zapíše do konzoly.  Jinak, pokud **vstup pro čtení** aktivity neobdrží data v přiděleném čase, pak budou zrušeny a zprávu vypršení časového limitu se zapíšou do konzoly.  Toto je běžný vzor použít k přidání vypršení časového limitu na každou akci.  
  
 ![Vyberte aktivitu](../../../docs/framework/windows-workflow-foundation/media/pickconceptual.JPG "PickConceptual")  
  
## <a name="best-practices"></a>Doporučené postupy  
 Při použití vybrat, větve, které provádí je větve, jejíž aktivační událost nejprve dokončí.  Koncepčně paralelně provádět všechny aktivační události a jedna aktivační událost může mít provést většinu svou logikou předtím, než je byla zrušena na dokončení jiné aktivační události.  Myslete na to obecných pokynů při používání vybrat aktivity je aktivační událost považovat za představující jednu událost a put jako málo logiku nejblíže do ní.  V ideálním případě aktivační událost musí obsahovat přesně akorát logiku přijímat události a veškeré zpracování této události by měli přejít do akce větve.  Tato metoda minimalizuje množství překryv mezi spuštění aktivačních událostí.  Představte si třeba <xref:System.Activities.Statements.Pick> s dvěma aktivačních událostí, kde jednotlivé aktivační události obsahuje <xref:System.ServiceModel.Activities.Receive> aktivity následuje další logiku.  Pokud další logiku zavádí bod nečinnosti, pak je možné, i <xref:System.ServiceModel.Activities.Receive> úspěšném dokončení aktivity.  Jedna aktivační událost se plně dokončení při jiné bude nedokončeným.  V některých případech nepřijatelná přijímá zprávy a částečně dokončení zpracování se.  Proto při používání předdefinovaných zasílání zpráv aktivity WF, jako <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>, zatímco <xref:System.ServiceModel.Activities.Receive> se často používá v aktivační události, <xref:System.ServiceModel.Activities.SendReply> a jiné logiky měly být umístěny v akci, kdykoli je to možné.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Pomocí vybrat aktivity v Návrháři  
 Pokud chcete použít vybrat v návrháři, Najít **vyberte** a **PickBranch** v panelu nástrojů.  Přetáhnout myší **vyberte** na plátno.  Ve výchozím nastavení nový **vyberte** aktivity v návrháři bude obsahovat dvě větve.  Chcete-li přidat další větve, přetáhněte **PickBranch** aktivity a umístěte jej vedle existující větve. Aktivity může být přetažen na **vyberte** aktivity do buď **aktivační událost** oblasti nebo **akce** oblasti kterékoli **PickBranch**.  
  
## <a name="using-the-pick-activity-in-code"></a>Pomocí aktivity vyberte v kódu  
 <xref:System.Activities.Statements.Pick> Aktivita se používá naplněním jeho <xref:System.Activities.Statements.Pick.Branches%2A> kolekce s <xref:System.Activities.Statements.PickBranch> aktivity. <xref:System.Activities.Statements.PickBranch> Aktivity každý mít <xref:System.Activities.Statements.PickBranch.Trigger%2A> vlastnost typu <xref:System.Activities.Activity>. Po dokončení provádění zadaná aktivita <xref:System.Activities.Statements.PickBranch.Action%2A> provede.  
  
 Následující příklad kódu ukazuje, jak používat <xref:System.Activities.Statements.Pick> aktivity k implementaci vypršení časového limitu pro aktivitu, která přečte řádek z konzoly.  
  
```csharp  
Sequence body = new Sequence()  
{  
    Variables = { name },  
    Activities =   
   {  
       new System.Activities.Statements.Pick  
        {  
           Branches =   
           {  
               new PickBranch  
               {  
                   Trigger = new ReadLine  
                   {  
                      Result = name,  
                      BookmarkName = "name"  
                   },  
                   Action = new WriteLine   
                   {   
                       Text = ExpressionServices.Convert<string>(ctx => "Hello " +   
                           name.Get(ctx))   
                   }  
               },  
               new PickBranch  
               {  
                   Trigger = new Delay  
                   {  
                      Duration = new TimeSpan(0, 0, 5)  
                   },  
                   Action = new WriteLine  
                   {  
                      Text = "Time is up."  
                   }  
               }  
           }  
       }  
   }  
};  
```  
  
```xaml  
<Sequence xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <Variable x:TypeArguments="x:String" Name="username" />  
  </Sequence.Variables>  
  <Pick>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <ReadLine BookmarkName="name" Result="username" />  
      </PickBranch.Trigger>  
      <WriteLine>[String.Concat("Hello ", username)]</WriteLine>  
    </PickBranch>  
    <PickBranch>  
      <PickBranch.Trigger>  
        <Delay>00:00:05</Delay>  
      </PickBranch.Trigger>  
      <WriteLine>Time is up.</WriteLine>  
    </PickBranch>  
  </Pick>  
</Sequence>  
```

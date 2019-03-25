---
title: Výběr aktivity
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: b9ee6c06377760d27bc54d39c1d1f3ecf67ea0d8
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409988"
---
# <a name="pick-activity"></a>Výběr aktivity
<xref:System.Activities.Statements.Pick> Aktivity zjednodušuje modelování sadu triggerů událostí a jejich odpovídající obslužné rutiny.  A <xref:System.Activities.Statements.Pick> aktivita obsahuje kolekci <xref:System.Activities.Statements.PickBranch> aktivity, ve kterém každý <xref:System.Activities.Statements.PickBranch> je párování mezi <xref:System.Activities.Statements.PickBranch.Trigger%2A> aktivity a <xref:System.Activities.Statements.PickBranch.Action%2A> aktivity.  V době spuštění aktivační události pro všechny větve spouští paralelně.  Po dokončení jednu aktivační událost, pak je její odpovídající akci provést, a další triggery se zruší.  Chování [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> aktivity se podobá [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] <xref:System.Workflow.Activities.ListenActivity> aktivity.  
  
 Na následujícím snímku obrazovky z [pomocí aktivity vyberte](./samples/using-the-pick-activity.md) SDK – ukázka ukazuje aktivitě Pick se dvě větve.  Jedna větev obsahuje trigger s názvem **čtení vstup**, vlastní aktivitu, která načte vstup z příkazového řádku. Druhý větev <xref:System.Activities.Statements.Delay> aktivační událost pro aktivitu. Pokud **čtení vstup** aktivita přijímá data před <xref:System.Activities.Statements.Delay> dokončení aktivity <xref:System.Activities.Statements.Delay> zruší zpoždění a pozdrav se zapíše do konzoly.  Jinak, pokud **čtení vstup** aktivity nedostane data v přiděleném čase, pak se zruší a časový limit zprávy, se zapíšou do konzoly.  To se běžně používá k přidání vypršení časového limitu na každou akci.  
  
 ![Výběr aktivity](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a>Osvědčené postupy  
 Při použití výběru, je větev, která spustí větev, jejíž aktivační událost dokončení první.  Koncepčně paralelně spustit všechny aktivační události a jedna aktivační událost může mít provedeny většinou svou logikou předtím, než ji zruší dokončení další trigger.  Myslete na to obecných pokynů při použití aktivity Pick se bude považovat aktivační událost jako jedna událost a vložit jako malé logikou, jako je to možné do něj.  V ideálním případě aktivační událost může obsahovat jenom dostatek logiku pro přijetí události a veškeré zpracování této události by měly patřit do akce větve.  Tato metoda minimalizuje množství překrytí spuštění aktivační události.  Představte si třeba <xref:System.Activities.Statements.Pick> s dvěma aktivačními procedurami, kde každá aktivační událost obsahuje <xref:System.ServiceModel.Activities.Receive> aktivity za nímž následuje další logiku.  Pokud nečinnosti bodu zavádí další logiku, pak je možné obou <xref:System.ServiceModel.Activities.Receive> úspěšném dokončení aktivity.  Jedna aktivační událost se plně kompletní při jiné se částečně dokončeno.  V některých případech nepřijatelné přijímat zprávy a potom částečně dokončí zpracování.  Proto při použití předdefinovaných zasílání zpráv aktivity WF, jako <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>, zatímco <xref:System.ServiceModel.Activities.Receive> se běžně používá v triggeru, <xref:System.ServiceModel.Activities.SendReply> a další logiky měly být umístěny v akci, kdykoli je to možné.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Použití aktivity Pick v Návrháři  
 Použijte výběr v návrháři, Najít **vyberte** a **PickBranch** na panelu nástrojů.  Přetáhnout myší **vyberte** na plátno.  Ve výchozím nastavení nový **vyberte** aktivity v návrháři bude obsahovat dvě větve.  Chcete-li přidat další větve, přetáhněte **PickBranch** aktivity a umístěte ho vedle existující větve. Aktivity může být přetaženy **vyberte** aktivitu buď **aktivační událost** oblasti nebo **akce** oblasti kterékoli **PickBranch**.  
  
## <a name="using-the-pick-activity-in-code"></a>Použití aktivity vybrat v kódu  
 <xref:System.Activities.Statements.Pick> Aktivita používá naplnění jeho <xref:System.Activities.Statements.Pick.Branches%2A> kolekce s <xref:System.Activities.Statements.PickBranch> aktivity. <xref:System.Activities.Statements.PickBranch> Každé aktivity mají <xref:System.Activities.Statements.PickBranch.Trigger%2A> vlastnost typu <xref:System.Activities.Activity>. Po dokončení provádění, zadané aktivita <xref:System.Activities.Statements.PickBranch.Action%2A> spustí.  
  
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

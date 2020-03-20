---
title: Výběr aktivity
ms.date: 03/30/2017
ms.assetid: b3e49b7f-0285-4720-8c09-11ae18f0d53e
ms.openlocfilehash: 672de5fd3df5e8dde6c54118503bf2a11353b116
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182897"
---
# <a name="pick-activity"></a>Výběr aktivity
Aktivita <xref:System.Activities.Statements.Pick> zjednodušuje modelování sady aktivačních událostí následovaných odpovídajícími obslužnými rutinami.  Aktivita <xref:System.Activities.Statements.Pick> <xref:System.Activities.Statements.PickBranch> obsahuje kolekci aktivit, <xref:System.Activities.Statements.PickBranch> kde každý je <xref:System.Activities.Statements.PickBranch.Trigger%2A> párování <xref:System.Activities.Statements.PickBranch.Action%2A> mezi aktivitou a aktivitou.  V době spuštění aktivační události pro všechny větve jsou prováděny paralelně.  Po dokončení jedné aktivační události je provedena odpovídající akce a všechny ostatní aktivační události jsou zrušeny.  Chování aktivity [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <xref:System.Activities.Statements.Pick> je podobné aktivitě rozhraní .NET Framework 3.5. <xref:System.Workflow.Activities.ListenActivity>  
  
 Následující snímek obrazovky z [ukázky Použití vyskladnění aktivity](./samples/using-the-pick-activity.md) SDK zobrazuje aktivitu vyskladnění se dvěma větvemi.  Jedna větev má aktivační událost nazvanou **Vstup pro čtení**, vlastní aktivitu, která čte vstup z příkazového řádku. Druhá větev <xref:System.Activities.Statements.Delay> má aktivační událost aktivity. Pokud **čtení vstupní** aktivity obdrží <xref:System.Activities.Statements.Delay> data před <xref:System.Activities.Statements.Delay> dokončením aktivity Delay bude zrušena a bude zapsán pozdrav do konzoly.  V opačném případě pokud **čtení vstupní** aktivity nepřijímá data v přiděleném čase, pak bude zrušena a zpráva o časovém odhlášení bude zapsána do konzoly.  Toto je běžný vzor, který se používá k přidání časového opovce pro libovolnou akci.  
  
 ![Výběr aktivity](./media/pick-activity/pick-activity-two-branches.jpg)  
  
## <a name="best-practices"></a>Osvědčené postupy  
 Při použití Vyskladnění je větev, která se spustí, větev, jejíž aktivační událost se dokončí jako první.  Koncepčně všechny aktivační události spustit paralelně a jeden aktivační událost může mít provedeny většinu jeho logiky před zrušením dokončení jiné aktivační události.  S ohledem na to obecné vodítko následovat při použití pick aktivity je považovat aktivační událost jako představující jednu událost a dát co nejméně logiky, jak je to možné do něj.  V ideálním případě aktivační událost by měla obsahovat pouze dostatek logiky pro příjem události a všechny zpracování této události by měl přejít do akce větve.  Tato metoda minimalizuje množství překrytí mezi provádění aktivačních událostí.  Zvažte například <xref:System.Activities.Statements.Pick> s dvěma aktivačními událostmi, kde každá aktivační událost obsahuje aktivitu <xref:System.ServiceModel.Activities.Receive> následovanou další logikou.  Pokud další logika zavádí bod nečinnosti, pak <xref:System.ServiceModel.Activities.Receive> je možnost obě aktivity dokončení úspěšně.  Jedna aktivační událost bude plně dokončena, zatímco druhá bude částečně dokončena.  V některých případech přijetí zprávy a potom částečné dokončení zpracování je nepřijatelné.  Proto při použití wf integrované zasílání zpráv <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply>aktivity, jako je například a , zatímco <xref:System.ServiceModel.Activities.Receive> se běžně používá v aktivační události <xref:System.ServiceModel.Activities.SendReply> a další logika by měla být uvedena v akci, kdykoli je to možné.  
  
## <a name="using-the-pick-activity-in-the-designer"></a>Použití aktivity vyskladnění v návrháři  
 Chcete-li použít Pick v návrháři, **najděte** pick a **pickbranch** v panelu nástrojů.  Přetáhněte na plátno **vyberte.**  Ve výchozím nastavení bude nová aktivita **vyskladnění** v návrháři obsahovat dvě větve.  Chcete-li přidat další větve, přetáhněte aktivitu **PickBranch** a přetáhněte ji vedle existujících větví. Aktivity mohou být vynechány na **aktivitu vyskladnění** do oblasti **Trigger** nebo do oblasti **akce** libovolné **větve pickbranch**.  
  
## <a name="using-the-pick-activity-in-code"></a>Použití aktivity vyskladnění v kódu  
 Aktivita se <xref:System.Activities.Statements.Pick> používá vyplněním <xref:System.Activities.Statements.Pick.Branches%2A> své <xref:System.Activities.Statements.PickBranch> sbírky aktivitami. Aktivity <xref:System.Activities.Statements.PickBranch> každý <xref:System.Activities.Statements.PickBranch.Trigger%2A> mají vlastnost <xref:System.Activities.Activity>typu . Po dokončení provádění zadané aktivity provede. <xref:System.Activities.Statements.PickBranch.Action%2A>  
  
 Následující příklad kódu ukazuje, jak <xref:System.Activities.Statements.Pick> použít aktivitu k implementaci časového období pro aktivitu, která čte řádek z konzoly.  
  
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

---
title: kompenzace
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 504c6b9efc3ca238d5cfcaa8bc7b72b4a40a3334
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compensation"></a>kompenzace
Náhrada v systému Windows Workflow Foundation (WF) je mechanismus, pomocí kterého dříve dokončené práce odvolat nebo kompenzované (následující logiky definované aplikací.) Pokud dojde k následující chybě. Tato část popisuje postup použití kompenzace v pracovních postupech.  
  
## <a name="compensation-vs-transactions"></a>Kompenzace vs. Transakce  
 Transakce můžete kombinovat více operací do jedné jednotky práce. Pomocí transakce dává možnost přerušit všechny změny, které jsou spuštěny uvnitř transakce při výskytu chyby během libovolná součást procesu transakce (pouze vrácení) vaší aplikace. Použití transakcí však nemusí být vhodné v případě práce dlouho spuštěný. Například cesta plánování aplikace je implementováno jako pracovní postup. Rezervace letu, čekají na schválení správce a pak platícího pro letu může obsahovat kroky pracovního postupu. Tento proces může trvat dlouho a není praktické kroky rezervace a platebního pro let k účasti ve stejné transakci. Ve scénáři jako je tato kompenzace může vrátit zpět rezervaci krok pracovního postupu, pokud dojde k selhání později ve zpracování.  
  
> [!NOTE]
>  Toto téma popisuje kompenzace v pracovních postupech. Další informace o transakcích v pracovních postupech najdete v tématu [transakce](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) a <xref:System.Activities.Statements.TransactionScope>. Další informace o transakcích najdete v tématu <xref:System.Transactions?displayProperty=nameWithType> a <xref:System.Transactions.Transaction?displayProperty=nameWithType>.  
  
## <a name="using-compensableactivity"></a>Pomocí CompensableActivity  
 <xref:System.Activities.Statements.CompensableActivity> je základní kompenzace aktivity v [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Všech aktivit, které provádějí práci, kterou muset kompenzovat se umístí do <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity>. V tomto příkladu je umístěn krok rezervace nákup cestě do <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> a zrušení rezervace je umístěn do <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>. Hned <xref:System.Activities.Statements.CompensableActivity> v pracovním postupu jsou dvě aktivity, které čekat na schválení správce a pak dokončete nákupu krok letu. Pokud se chybová podmínka způsobí, že v pracovním postupu zrušit po <xref:System.Activities.Statements.CompensableActivity> bylo úspěšně dokončeno, pak aktivity v <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> jsou naplánovány obslužné rutiny a zrušení letu.  
  
 [!code-csharp[CFX_CompensationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 V následujícím příkladu je pracovní postup v jazyce XAML.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 Po vyvolání pracovního postupu se zobrazí následující výstup do konzoly.  
  
 **ReserveFlight: Lístku je vyhrazena.**  
**ManagerApproval: Schválení správce přijata.**   
**PurchaseFlight: Lístku je zakoupili.**   
**Pracovního postupu byla úspěšně dokončena se stavem: uzavřen.**    
> [!NOTE]
>  Ukázkové aktivity v tomto tématu, jako `ReserveFlight` pro konzolu tak, aby usnadnily vyjádření pořadí, ve kterém jsou prováděny aktivity, když dojde k kompenzace zobrazit jejich název a účel.  
  
### <a name="default-workflow-compensation"></a>Výchozí kompenzace pracovního postupu  
 Ve výchozím nastavení Pokud pracovní postup se zruší, logice kompenzace se spouští compensable aktivit, které má úspěšně úplně a již není potvrzena nebo kompenzované.  
  
> [!NOTE]
>  Když <xref:System.Activities.Statements.CompensableActivity> je *potvrzen*, kompenzace aktivity již nelze vyvolat. Proces potvrzení najdete dál v této části.  
  
 V tomto příkladu je vyvolána výjimka po letu je vyhrazena, ale před krokem schválení správce.  
  
 [!code-csharp[CFX_CompensationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 V tomto příkladu je pracovní postup v jazyce XAML.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:SimulatedErrorCondition />  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 [!code-csharp[CFX_CompensationExample#100](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 Po vyvolání pracovního postupu je simulované chyba podmínku výjimka ošetřena hostitele aplikací v <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, pracovní postup se zruší a logiku kompenzace je volána.  
  
 **ReserveFlight: Lístku je vyhrazena.**  
**SimulatedErrorCondition: Vyvolání ApplicationException –.**   
**Pracovní postup neošetřená výjimka:**   
**System.ApplicationException: Simulované chybový stav v pracovním postupu.**   
**CancelFlight: Lístku je zrušena.**   
**Pracovního postupu byla úspěšně dokončena se stavem: zrušena.**    
### <a name="cancellation-and-compensableactivity"></a>Zrušení a CompensableActivity  
 Pokud aktivity v <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> mít není dokončeno a zrušení aktivity aktivity v <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> provedení.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Je volána, pouze pokud aktivity v <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> nedokončili a zrušení aktivity. <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Je spustit pouze pokud aktivity v <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> úspěšně dokončena a kompenzace je následně vyvolána na aktivity.  
  
 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Dává možnost poskytnout všechny příslušné zrušení logiku autoři pracovního postupu. V následujícím příkladu, je vyvolána výjimka při provádění <xref:System.Activities.Statements.CompensableActivity.Body%2A>a potom <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> je volána.  
  
```csharp  
Activity wf = new Sequence()  
{  
    Activities =  
    {  
        new CompensableActivity  
        {  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new ChargeCreditCard(),  
                    new SimulatedErrorCondition(),  
                    new ReserveFlight()  
                }  
            },  
            CompensationHandler = new CancelFlight(),  
            CancellationHandler = new CancelCreditCard()  
        },  
        new ManagerApproval(),  
        new PurchaseFlight()  
    }  
};  
```  
  
 V tomto příkladu je pracovní postup v jazyce XAML  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken" />  
    </CompensableActivity.Result>  
    <Sequence>  
      <c:ChargeCreditCard />  
      <c:SimulatedErrorCondition />  
      <c:ReserveFlight />  
    </Sequence>  
    <CompensableActivity.CancellationHandler>  
      <c:CancelCreditCard />  
    </CompensableActivity.CancellationHandler>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
</Sequence>  
```  
  
 Po vyvolání pracovního postupu je simulované chyba podmínku výjimka ošetřena hostitele aplikací v <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, zrušení pracovního postupu a zrušení logiku <xref:System.Activities.Statements.CompensableActivity> je volána. V tomto příkladu kompenzace logiku a logiku zrušení mít jiné cíle. Pokud <xref:System.Activities.Statements.CompensableActivity.Body%2A> úspěšně dokončit, pak to znamená byl účtovat platební karty, letu zaznamenán, takže vyrovnání by měl vrátit oba kroky. (V tomto příkladu zrušení letu automaticky zruší poplatky platební karty.) Ale pokud <xref:System.Activities.Statements.CompensableActivity> se zruší, to znamená <xref:System.Activities.Statements.CompensableActivity.Body%2A> nebyla úplný a tak logiku <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> musí být schopní určit, jak nejlépe zpracovat zrušení. V tomto příkladu <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> zruší poplatků platební karty, ale od té doby `ReserveFlight` byl poslední aktivita v <xref:System.Activities.Statements.CompensableActivity.Body%2A>, se nebude pokoušet o zrušení letu. Vzhledem k tomu `ReserveFlight` byl poslední aktivita v <xref:System.Activities.Statements.CompensableActivity.Body%2A>, pokud bylo úspěšně dokončeno potom <xref:System.Activities.Statements.CompensableActivity.Body%2A> by dokončili a žádné zrušení by bylo možné.  
  
 **ChargeCreditCard: Poplatků platební karty pro let.**  
**SimulatedErrorCondition: Vyvolání ApplicationException –.**   
**Pracovní postup neošetřená výjimka:**   
**System.ApplicationException: Simulované chybový stav v pracovním postupu.**   
**CancelCreditCard: Zrušit poplatky platební karty.**   
**Pracovního postupu byla úspěšně dokončena se stavem: zrušena.**  Další informace o zrušení najdete v tématu [zrušení](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Pomocí explicitní kompenzace odpovídajícím způsobem aktivity  
 V předchozím oddílu byla zahrnutých implicitní honoráře. Implicitní kompenzace může být vhodné pro jednoduchého scénáře, ale pokud podrobnější je potřeba řízení nad plánováním kompenzace pak zpracování <xref:System.Activities.Statements.Compensate> lze aktivity. Zahájíte proces kompenzace <xref:System.Activities.Statements.Compensate> aktivity, <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> pro které kompenzace se požaduje se používá. <xref:System.Activities.Statements.Compensate> Aktivity lze použít k zahájení kompenzace na žádném Dokončit <xref:System.Activities.Statements.CompensableActivity> které nebyly potvrzeny ani kompenzované. Například <xref:System.Activities.Statements.Compensate> aktivity může být používány <xref:System.Activities.Statements.TryCatch.Catches%2A> části <xref:System.Activities.Statements.TryCatch> aktivity nebo kdykoli po dokončení <xref:System.Activities.Statements.CompensableActivity> byla dokončena. V tomto příkladu <xref:System.Activities.Statements.Compensate> aktivita se používá v <xref:System.Activities.Statements.TryCatch.Catches%2A> části <xref:System.Activities.Statements.TryCatch> aktivitu pro vrácení akce <xref:System.Activities.Statements.CompensableActivity>.  
  
 [!code-csharp[CFX_CompensationExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 V tomto příkladu je pracovní postup v jazyce XAML.  
  
```xaml  
<TryCatch  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:s="clr-namespace:System;assembly=mscorlib"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <TryCatch.Variables>  
    <Variable  
       x:TypeArguments="CompensationToken"  
       x:Name="__ReferenceID0"  
       Name="token1" />  
  </TryCatch.Variables>  
  <TryCatch.Try>  
    <Sequence>  
      <CompensableActivity>  
        <CompensableActivity.Result>  
          <OutArgument  
             x:TypeArguments="CompensationToken">  
            <VariableReference  
               x:TypeArguments="CompensationToken"  
               Variable="{x:Reference __ReferenceID0}">  
              <VariableReference.Result>  
                <OutArgument  
                   x:TypeArguments="Location(CompensationToken)" />  
              </VariableReference.Result>  
            </VariableReference>  
          </OutArgument>  
        </CompensableActivity.Result>  
        <CompensableActivity.CompensationHandler>  
          <c:CancelFlight />  
        </CompensableActivity.CompensationHandler>  
        <CompensableActivity.ConfirmationHandler>  
          <c:ConfirmFlight />  
        </CompensableActivity.ConfirmationHandler>  
        <c:ReserveFlight />  
      </CompensableActivity>  
      <c:SimulatedErrorCondition />  
      <c:ManagerApproval />  
      <c:PurchaseFlight />  
    </Sequence>  
  </TryCatch.Try>  
  <TryCatch.Catches>  
    <Catch  
       x:TypeArguments="s:ApplicationException">  
      <ActivityAction  
         x:TypeArguments="s:ApplicationException">  
        <Compensate>  
          <Compensate.Target>  
            <InArgument  
               x:TypeArguments="CompensationToken">  
              <VariableValue  
                 x:TypeArguments="CompensationToken"  
                 Variable="{x:Reference __ReferenceID0}">  
                <VariableValue.Result>  
                  <OutArgument  
                     x:TypeArguments="CompensationToken" />  
                </VariableValue.Result>  
              </VariableValue>  
            </InArgument>  
          </Compensate.Target>  
        </Compensate>  
      </ActivityAction>  
    </Catch>  
  </TryCatch.Catches>  
</TryCatch>  
```  
  
 Po vyvolání pracovního postupu se zobrazí následující výstup do konzoly.  
  
 **ReserveFlight: Lístku je vyhrazena.**  
**SimulatedErrorCondition: Vyvolání ApplicationException –.**   
**CancelFlight: Lístku je zrušena.**   
**Pracovního postupu byla úspěšně dokončena se stavem: uzavřen.**    
### <a name="confirming-compensation"></a>Potvrzení kompenzace  
 Ve výchozím nastavení může být compensable aktivity vyrovnávat kdykoli po jejich dokončení. V některých případech to nemusí být vhodné. V předchozím příkladu vyrovnání pro rezervování lístek se o zrušení vyhrazení. Po dokončení letu tento krok kompenzace je však již nebude platný. Potvrzení compensable aktivity volá aktivita určeného <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>. Možné použití pro tuto je umožnit všechny prostředky, které jsou nezbytné k provedení náhrady k uvolnění. Po compensable aktivity je potvrzen, není možné pro něj má být nahrazeno a pokud je tento pokus <xref:System.InvalidOperationException> je vyvolána výjimka. Po úspěšném dokončení pracovního postupu jsou všechny nepotvrzené a kompenzované compensable aktivity, které byl úspěšně dokončen v obráceném pořadí potvrdit dokončení. V tomto příkladu je letu vyhrazené, zakoupených a dokončení a potom je potvrzen compensable aktivity. Potvrďte <xref:System.Activities.Statements.CompensableActivity>, použijte <xref:System.Activities.Statements.Confirm> aktivity a zadejte <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> potvrďte.  
  
 [!code-csharp[CFX_CompensationExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 V tomto příkladu je pracovní postup v jazyce XAML.  
  
```xaml  
<Sequence  
   xmlns="http://schemas.microsoft.com/netfx/2009/xaml/activities"  
   xmlns:c="clr-namespace:CompensationExample;assembly=CompensationExample"  
   xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">  
  <Sequence.Variables>  
    <x:Reference>__ReferenceID0</x:Reference>  
  </Sequence.Variables>  
  <CompensableActivity>  
    <CompensableActivity.Result>  
      <OutArgument  
         x:TypeArguments="CompensationToken">  
        <VariableReference  
           x:TypeArguments="CompensationToken">  
          <VariableReference.Result>  
            <OutArgument  
               x:TypeArguments="Location(CompensationToken)" />  
          </VariableReference.Result>  
          <VariableReference.Variable>  
            <Variable  
               x:TypeArguments="CompensationToken"  
               x:Name="__ReferenceID0"  
               Name="token1" />  
          </VariableReference.Variable>  
        </VariableReference>  
      </OutArgument>  
    </CompensableActivity.Result>  
    <CompensableActivity.CompensationHandler>  
      <c:CancelFlight />  
    </CompensableActivity.CompensationHandler>  
    <CompensableActivity.ConfirmationHandler>  
      <c:ConfirmFlight />  
    </CompensableActivity.ConfirmationHandler>  
    <c:ReserveFlight />  
  </CompensableActivity>  
  <c:ManagerApproval />  
  <c:PurchaseFlight />  
  <c:TakeFlight />  
  <Confirm>  
    <Confirm.Target>  
      <InArgument  
         x:TypeArguments="CompensationToken">  
        <VariableValue  
           x:TypeArguments="CompensationToken"  
           Variable="{x:Reference __ReferenceID0}">  
          <VariableValue.Result>  
            <OutArgument  
               x:TypeArguments="CompensationToken" />  
          </VariableValue.Result>  
        </VariableValue>  
      </InArgument>  
    </Confirm.Target>  
  </Confirm>  
</Sequence>  
```  
  
 Po vyvolání pracovního postupu se zobrazí následující výstup do konzoly.  
  
 **ReserveFlight: Lístku je vyhrazena.**  
**ManagerApproval: Schválení správce přijata.**   
**PurchaseFlight: Lístku je zakoupili.**   
**TakeFlight: Letu byla dokončena.**   
**ConfirmFlight: Letu nebyla provedena, žádné honoráře možné.**   
**Pracovního postupu byla úspěšně dokončena se stavem: uzavřen.**   
## <a name="nesting-compensation-activities"></a>Vnoření kompenzace aktivity  
 A <xref:System.Activities.Statements.CompensableActivity> náleží do <xref:System.Activities.Statements.CompensableActivity.Body%2A> části jiného <xref:System.Activities.Statements.CompensableActivity>. A <xref:System.Activities.Statements.CompensableActivity> nemusí být umístěny do obslužnou rutinu jiného <xref:System.Activities.Statements.CompensableActivity>. Je zodpovědností nadřazený <xref:System.Activities.Statements.CompensableActivity> zajistit, že, pokud je zrušen, potvrzení nebo kompenzované, všechny aktivity compensable podřízené, které byly úspěšně dokončeny a není již byly potvrzen nebo kompenzované musí být potvrzen nebo vyrovnávat před dokončením nadřazené zrušení, potvrzení nebo honoráře. Pokud to není explicitně modelován nadřazené <xref:System.Activities.Statements.CompensableActivity> budou implicitně odpovídajícím způsobem podřízené compensable aktivity, pokud nadřazená přijme Storno nebo odpovídajícím způsobem signál. Pokud nadřazená přijala signál potvrdit nadřazené potvrdí implicitně podřízené compensable aktivity. Pokud logiku pro zpracování zrušení, potvrzení nebo kompenzace je explicitně modelován v obslužné rutině nadřazené <xref:System.Activities.Statements.CompensableActivity>, budou implicitně potvrzen všechny podřízené není explicitně zpracovávat.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Statements.CompensableActivity>  
 <xref:System.Activities.Statements.Compensate>  
 <xref:System.Activities.Statements.Confirm>  
 <xref:System.Activities.Statements.CompensationToken>  
 [Kompenzovatelná aktivita](../../../docs/framework/windows-workflow-foundation/samples/compensable-activity-sample.md)

---
title: Kompenzace
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 75c5ed2f5e5c3a93834632ce499a2c8195fbc6bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183005"
---
# <a name="compensation"></a>Kompenzace
Kompenzace v základech pracovních postupů systému Windows (WF) je mechanismus, kterým lze dříve dokončenou práci vrátit zpět nebo kompenzovat (podle logiky definované aplikací) při následné chybě. Tato část popisuje použití kompenzace v pracovních postupech.  
  
## <a name="compensation-vs-transactions"></a>Kompenzace vs. transakce  
 Transakce umožňuje kombinovat více operací do jedné jednotky práce. Použití transakce dává vaší aplikaci možnost přerušit (vrátit zpět) všechny změny provedené v rámci transakce, pokud dojde k chybám během jakékoli části procesu transakce. Použití transakcí však nemusí být vhodné, pokud je práce dlouho spuštěna. Například aplikace plánování cesty je implementována jako pracovní postup. Kroky pracovního postupu se mohou skládat z rezervace letu, čekání na schválení manažerem a následné platby za let. Tento proces může trvat mnoho dní a není praktické, aby se kroky rezervace a placení za let účastnily stejné transakce. V takovém případě může být kompenzace použita k vrácení kroku rezervace pracovního postupu, pokud dojde k selhání později při zpracování.  
  
> [!NOTE]
> Toto téma popisuje kompenzace v pracovních postupech. Další informace o transakcích v pracovních <xref:System.Activities.Statements.TransactionScope>postupech naleznete v [tématu Transakce](workflow-transactions.md) a . Další informace o transakcích <xref:System.Transactions?displayProperty=nameWithType> <xref:System.Transactions.Transaction?displayProperty=nameWithType>naleznete v tématu a .  
  
## <a name="using-compensableactivity"></a>Použití compensableActivity  
 <xref:System.Activities.Statements.CompensableActivity>je hlavní kompenzační [!INCLUDE[wf1](../../../includes/wf1-md.md)]činností v oblasti . Všechny činnosti, které vykonávají práci, kterou může <xref:System.Activities.Statements.CompensableActivity.Body%2A> být <xref:System.Activities.Statements.CompensableActivity>nutné kompenzovat, jsou umístěny do . V tomto příkladu je rezervační krok nákupu <xref:System.Activities.Statements.CompensableActivity.Body%2A> letu <xref:System.Activities.Statements.CompensableActivity> umístěn do a a zrušení <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>rezervace je umístěno do . Bezprostředně následující <xref:System.Activities.Statements.CompensableActivity> v pracovním postupu jsou dvě aktivity, které čekají na schválení manažera a pak dokončí nákupní krok letu. Pokud chybový stav způsobí, že pracovní <xref:System.Activities.Statements.CompensableActivity> postup bude zrušen po úspěšném dokončení, jsou naplánovány aktivity v <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> obslužné rutině a let je zrušen.  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 Následující příklad je pracovní postup v XAML.  
  
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
  
 Při vyvolání pracovního postupu se zobrazí následující výstup konzoly.  
  
 **ReserveFlight: Vstupenka je rezervována.**  
**Schválení manažera: Bylo přijato schválení správcem.** 
 **PurchaseFlight: Vstupenka je zakoupena.** 
 **Pracovní postup byl úspěšně dokončen se stavem: Uzavřeno.**
> [!NOTE]
> Ukázkové aktivity v `ReserveFlight` tomto tématu, jako je například zobrazení jejich název a účel konzoly pomoci ilustrovat pořadí, ve kterém jsou prováděny aktivity, když dojde k kompenzaci.  
  
### <a name="default-workflow-compensation"></a>Výchozí kompenzace pracovního postupu  
 Ve výchozím nastavení, pokud je pracovní postup zrušen, logika kompenzace je spuštěna pro všechny kompenzační aktivity, která byla úspěšně zcela a již nebyla potvrzena nebo kompenzována.  
  
> [!NOTE]
> Pokud <xref:System.Activities.Statements.CompensableActivity> je *a potvrzena*, nelze již vyvolat kompenzaci za aktivitu. Proces potvrzení je popsán dále v této části.  
  
 V tomto příkladu je vyvolána výjimka po letu je vyhrazena, ale před krokem schválení vedoucího.  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 Tento příklad je pracovní postup v XAML.  
  
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
  
 [!code-csharp[CFX_CompensationExample#100](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#100)]  
  
 Při vyvolání pracovního postupu je výjimka simulovaného chybového <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>stavu zpracována hostitelskou aplikací v aplikaci , pracovní postup je zrušen a je vyvolána logika kompenzace.  
  
 **ReserveFlight: Vstupenka je rezervována.**  
**SimulatedErrorCondition: Vyvolání applicationexception.** 
 **Neošetřená výjimka pracovního postupu:**
**System.ApplicationException: Simulovaná chybová podmínka v pracovním postupu.** 
 **CancelFlight: Letenka je zrušena.** 
 **Pracovní postup byl úspěšně dokončen se stavem: Zrušeno.**
### <a name="cancellation-and-compensableactivity"></a>Zrušení a kompenzační aktivita  
 Pokud aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A> v <xref:System.Activities.Statements.CompensableActivity> of a nebyly dokončeny a aktivita <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> je zrušena, aktivity v jsou prováděny.  
  
> [!NOTE]
> Je <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> vyvolána pouze v případě, že aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A> v rámci nebyly dokončeny <xref:System.Activities.Statements.CompensableActivity> a aktivita je zrušena. Je <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> proveden pouze v případě, <xref:System.Activities.Statements.CompensableActivity.Body%2A> že <xref:System.Activities.Statements.CompensableActivity> aktivity v mají úspěšně dokončena a kompenzace je následně vyvolána na aktivitu.  
  
 Poskytuje <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> autorům pracovního postupu možnost poskytnout odpovídající logiku zrušení. V následujícím příkladu je vyvolána výjimka <xref:System.Activities.Statements.CompensableActivity.Body%2A>během provádění <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , a potom je vyvolána.  
  
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
  
 Tento příklad je pracovní postup v XAML  
  
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
  
 Při vyvolání pracovního postupu je výjimka simulovaného chybového <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>stavu zpracována hostitelskou aplikací v <xref:System.Activities.Statements.CompensableActivity> aplikaci , pracovní postup je zrušen a je vyvolána logika zrušení. V tomto příkladu logiky kompenzace a zrušení logiky mají různé cíle. Pokud <xref:System.Activities.Statements.CompensableActivity.Body%2A> byl úspěšně dokončen, znamená to, že kreditní karta byla naúčtována a let rezervován, takže kompenzace by měla vrátit oba kroky. (V tomto příkladu zrušení letu automaticky zruší poplatky za kreditní kartu.) Však pokud <xref:System.Activities.Statements.CompensableActivity> je zrušena, to <xref:System.Activities.Statements.CompensableActivity.Body%2A> znamená, že nebyla <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> dokončena, a proto logika musí být schopen určit, jak nejlépe zpracovat zrušení. V tomto příkladu <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> zruší poplatek za `ReserveFlight` platební kartu, ale <xref:System.Activities.Statements.CompensableActivity.Body%2A>protože byla poslední aktivita v , se nepokouší zrušit let. Vzhledem k `ReserveFlight` tomu, <xref:System.Activities.Statements.CompensableActivity.Body%2A>že byla poslední aktivitou <xref:System.Activities.Statements.CompensableActivity.Body%2A> v oblasti , pokud by byla úspěšně dokončena, byla by dokončena a nebylo by možné zrušit.  
  
 **ChargeCreditCard: Strhávat kreditní kartu za let.**  
**SimulatedErrorCondition: Vyvolání applicationexception.** 
 **Neošetřená výjimka pracovního postupu:**
**System.ApplicationException: Simulovaná chybová podmínka v pracovním postupu.** 
 **CancelCreditCard: Zrušit poplatky za kreditní kartu.** 
 **Pracovní postup byl úspěšně dokončen se stavem: Zrušeno.**  Další informace o zrušení naleznete v tématu [Zrušení](modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Explicitní kompenzace pomocí kompenzované aktivity  
 V předchozí části byla pokryta implicitní kompenzace. Implicitní kompenzace může být vhodná pro jednoduché scénáře, ale pokud <xref:System.Activities.Statements.Compensate> je vyžadována více explicitní kontrola nad plánováním zpracování kompenzace, lze aktivitu použít. Chcete-li zahájit <xref:System.Activities.Statements.Compensate> proces kompenzace s aktivitou, <xref:System.Activities.Statements.CompensationToken> používá <xref:System.Activities.Statements.CompensableActivity> se pro které je požadována kompenzace. Aktivitu <xref:System.Activities.Statements.Compensate> lze použít k zahájení <xref:System.Activities.Statements.CompensableActivity> kompenzace za všechny dokončené, které nebyly potvrzeny nebo kompenzovány. Aktivita <xref:System.Activities.Statements.Compensate> může být například <xref:System.Activities.Statements.TryCatch.Catches%2A> použita <xref:System.Activities.Statements.TryCatch> v části aktivity <xref:System.Activities.Statements.CompensableActivity> nebo kdykoli po dokončení. V tomto příkladu se <xref:System.Activities.Statements.Compensate> aktivita používá v <xref:System.Activities.Statements.TryCatch.Catches%2A> části <xref:System.Activities.Statements.TryCatch> aktivity <xref:System.Activities.Statements.CompensableActivity>ke stornování akce .  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 Tento příklad je pracovní postup v XAML.  
  
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
  
 Při vyvolání pracovního postupu se zobrazí následující výstup konzoly.  
  
 **ReserveFlight: Vstupenka je rezervována.**  
**SimulatedErrorCondition: Vyvolání applicationexception.** 
 **CancelFlight: Letenka je zrušena.** 
 **Pracovní postup byl úspěšně dokončen se stavem: Uzavřeno.**
### <a name="confirming-compensation"></a>Potvrzení kompenzace  
 Ve výchozím nastavení mohou být kompenzační aktivity kompenzovány kdykoli po jejich dokončení. V některých případech to nemusí být vhodné. V předchozím příkladu bylo kompenzací za rezervaci letenky zrušení rezervace. Po dokončení letu však tento kompenzační krok již není platný. Potvrzení kompenzační aktivity vyvolá aktivitu určenou <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>parametrem . Jedním z možných použití pro toto je umožnit všechny prostředky, které jsou nezbytné k provedení kompenzace, které mají být uvolněny. Po potvrzení kompenzační aktivity není možné, aby byla kompenzována, a pokud se <xref:System.InvalidOperationException> o to pokusíte, je vyvolána výjimka. Po úspěšném dokončení pracovního postupu jsou potvrzeny všechny nepotvrzené a nekompenzované kompenzační aktivity, které byly úspěšně dokončeny, v opačném pořadí dokončení. V tomto příkladu je let rezervován, zakoupen a dokončen a poté je potvrzena kompenzační aktivita. Chcete-li <xref:System.Activities.Statements.CompensableActivity>potvrdit <xref:System.Activities.Statements.Confirm> , použijte <xref:System.Activities.Statements.CompensationToken> aktivitu <xref:System.Activities.Statements.CompensableActivity> a zadejte potvrzení.  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 Tento příklad je pracovní postup v XAML.  
  
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
  
Při vyvolání pracovního postupu se zobrazí následující výstup konzoly.  
  
**ReserveFlight: Vstupenka je rezervována.**  
**Schválení manažera: Bylo přijato schválení správcem.** 
 **PurchaseFlight: Vstupenka je zakoupena.** 
 **TakeFlight: Let je dokončen.** 
 **ConfirmFlight: Let byl přijat, žádná kompenzace není možná.** 
 **Pracovní postup byl úspěšně dokončen se stavem: Uzavřeno.**

## <a name="nesting-compensation-activities"></a>Aktivity kompenzace vnoření  

A <xref:System.Activities.Statements.CompensableActivity> může být <xref:System.Activities.Statements.CompensableActivity.Body%2A> umístěn do <xref:System.Activities.Statements.CompensableActivity>sekce jiného . A <xref:System.Activities.Statements.CompensableActivity> nesmí být umístěndo obslužné rutiny jiného <xref:System.Activities.Statements.CompensableActivity>. Je odpovědností rodiče <xref:System.Activities.Statements.CompensableActivity> zajistit, aby při zrušení, potvrzení nebo kompenzaci byly všechny podřízené kompenzační činnosti, které úspěšně dokončily a které ještě nebyly potvrzeny nebo kompenzovány, potvrzeny nebo kompenzovány dříve, než rodič dokončí zrušení, potvrzení nebo náhradu. Pokud to není modelováno <xref:System.Activities.Statements.CompensableActivity> explicitně nadřazený bude implicitně kompenzovat podřízené kompenzační aktivity, pokud nadřazený obdržel signál cancel nebo kompenziční. Pokud rodič obdržel potvrzení signálu rodič implicitně potvrdí podřízené kompenzační činnosti. Pokud logika pro zpracování zrušení, potvrzení nebo kompenzace je <xref:System.Activities.Statements.CompensableActivity>explicitně modelován v obslužné rutině nadřazené , všechny podřízené není explicitně zpracována bude implicitně potvrzena.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>

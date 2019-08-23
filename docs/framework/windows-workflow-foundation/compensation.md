---
title: Kompenzace
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 147da26fd297d41876815cffcc70450ae905ba85
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935432"
---
# <a name="compensation"></a>Kompenzace
Kompenzace v programovací model Windows Workflow Foundation (WF) je mechanismus, pomocí kterého se dřív dokončená práce může vrátit zpátky nebo kompenzovat (podle logiky definované aplikací), když dojde k následnému selhání. V této části se dozvíte, jak používat kompenzace v pracovních postupech.  
  
## <a name="compensation-vs-transactions"></a>Kompenzace vs. Transakce  
 Transakce umožňuje kombinovat více operací do jediné pracovní jednotky. Použití transakce poskytuje vaší aplikaci možnost přerušení (vrácení zpět) všechny změny provedené v rámci transakce, pokud dojde k jakýmkoli chybám během jakékoli části procesu transakce. Použití transakcí ale nemusí být vhodné, pokud je práce dlouhodobě spuštěná. Například aplikace pro plánování cest je implementována jako pracovní postup. Kroky pracovního postupu se můžou skládat z rezervace letu, čekání na schválení manažera a pak za tento let platit. Tento proces může trvat mnoho dnů a není praktický pro kroky rezervace a placení za letu, aby se mohl zúčastnit stejné transakce. Ve scénářích, jako je to, je možné použít kompenzaci k vrácení kroku rezervace pracovního postupu, pokud dojde k selhání později během zpracování.  
  
> [!NOTE]
> Toto téma popisuje kompenzace v pracovních postupech. Další informace o transakcích v pracovních postupech najdete [](workflow-transactions.md) v tématu <xref:System.Activities.Statements.TransactionScope>transakce a. Další informace o transakcích naleznete v <xref:System.Transactions?displayProperty=nameWithType> tématu <xref:System.Transactions.Transaction?displayProperty=nameWithType>a.  
  
## <a name="using-compensableactivity"></a>Použití aktivita CompensableActivity  
 <xref:System.Activities.Statements.CompensableActivity>je základní aktivitou kompenzace [!INCLUDE[wf1](../../../includes/wf1-md.md)]v. Všechny aktivity, které provádějí práci, které mohou být potřeba kompenzovat, jsou umístěny do <xref:System.Activities.Statements.CompensableActivity.Body%2A> části <xref:System.Activities.Statements.CompensableActivity>. V tomto příkladu je krok rezervace při nákupu letu umístěný do <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> a a zrušení <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>rezervace se umístí do. Hned po <xref:System.Activities.Statements.CompensableActivity> dokončení pracovního postupu jsou dvě aktivity, které čekají na schválení manažerem a pak dokončí krok nákupu letu. Pokud chybový stav způsobí zrušení pracovního postupu po <xref:System.Activities.Statements.CompensableActivity> úspěšném dokončení, aktivity <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> v obslužné rutině se naplánují a let se zruší.  
  
 [!code-csharp[CFX_CompensationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
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
  
 Po vyvolání pracovního postupu se do konzoly zobrazí následující výstup.  
  
 **ReserveFlight: Lístek je rezervovaný.**  
**ManagerApproval: Bylo přijato schválení správcem.**    
**PurchaseFlight: Lístek je koupený.**    
**Pracovní postup byl úspěšně dokončen se stavem: Ukončit.**    
> [!NOTE]
> Ukázkové aktivity v tomto tématu, jako je `ReserveFlight` například zobrazení jejich názvu a účelu pro konzolu, aby pomohly objasnění pořadí, ve kterém jsou aktivity spouštěny, když dojde k kompenzaci.  
  
### <a name="default-workflow-compensation"></a>Výchozí kompenzace pracovního postupu  
 Ve výchozím nastavení platí, že pokud je pracovní postup zrušen, je logika kompenzace spuštěna pro všechny aktivity kompenzovatelná, které byly úspěšně dokončeny a dosud nebyly potvrzeny nebo vyrovnány.  
  
> [!NOTE]
> Pokud je potvrzeno, kompenzace aktivity již nelze vyvolat. <xref:System.Activities.Statements.CompensableActivity> Potvrzovací proces je popsán dále v této části.  
  
 V tomto příkladu je vyvolána výjimka po rezervaci letu, ale před krokem schválení vedoucího.  
  
 [!code-csharp[CFX_CompensationExample#2](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 Tento příklad je pracovní postup v jazyce XAML.  
  
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
  
 Při vyvolání pracovního postupu je výjimka simulované chybové podmínky zpracována hostitelskou aplikací v <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, pracovní postup je zrušen a je vyvolána logika kompenzace.  
  
 **ReserveFlight: Lístek je rezervovaný.**  
**SimulatedErrorCondition: Došlo k vyvolání ApplicationException.**    
**Neošetřená výjimka pracovního postupu:**    
**System. ApplicationException: Simulovaná chybová podmínka v pracovním postupu.**    
**CancelFlight: Lístek je zrušený.**    
**Pracovní postup byl úspěšně dokončen se stavem: Zrušil.**    
### <a name="cancellation-and-compensableactivity"></a>Zrušení a aktivita CompensableActivity  
 Pokud aktivity v <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> nástroji nejsou dokončeny a aktivita je zrušena <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> , aktivity v nástroji se spustí.  
  
> [!NOTE]
> Je vyvolána pouze v případě, že aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A> <xref:System.Activities.Statements.CompensableActivity> nejsou dokončeny a aktivita je zrušena. <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Je proveden pouze v případě, že aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A> v <xref:System.Activities.Statements.CompensableActivity> nástroji byly úspěšně dokončeny a náhrada je následně vyvolána u aktivity. <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>  
  
 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Dává autorům pracovního postupu možnost poskytnout jakoukoli vhodnou logiku zrušení. V následujícím příkladu je vyvolána výjimka během provádění <xref:System.Activities.Statements.CompensableActivity.Body%2A>a <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> poté je vyvolána.  
  
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
  
 Tento příklad je pracovní postup v jazyce XAML.  
  
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
  
 Při vyvolání pracovního postupu je vyvolána výjimka simulované chybové podmínky v <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>nástroji, pracovní postup je zrušen a logika <xref:System.Activities.Statements.CompensableActivity> zrušení je vyvolána. V tomto příkladu má logika kompenzace a logika zrušení různé cíle. Pokud se <xref:System.Activities.Statements.CompensableActivity.Body%2A> úspěšně dokončilo, znamená to, že se dal kreditní karta účtovat a zaúčtuje se let, takže by se měla kompenzace vrátit zpátky oběma kroky. (V tomto příkladu zrušení letu automaticky zruší poplatky za platební kartu.) Pokud <xref:System.Activities.Statements.CompensableActivity> je však zrušeno, znamená to, že se <xref:System.Activities.Statements.CompensableActivity.Body%2A> nedokončila, a <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> proto by logika potřeb měla být schopná určit, jak se má toto zrušení vymezit. V tomto příkladu <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> zruší poplatek za platební kartu, ale vzhledem `ReserveFlight` <xref:System.Activities.Statements.CompensableActivity.Body%2A>k tomu, že se jednalo o poslední aktivitu v, se nepokusí o zrušení letu. Vzhledem `ReserveFlight` k tomu <xref:System.Activities.Statements.CompensableActivity.Body%2A>, že se jednalo o poslední aktivitu v, pokud byla <xref:System.Activities.Statements.CompensableActivity.Body%2A> úspěšně dokončena, byl pravděpodobně dokončen a žádné zrušení by nebylo možné.  
  
 **ChargeCreditCard: Platební karta se účtuje pro let.**  
**SimulatedErrorCondition: Došlo k vyvolání ApplicationException.**    
**Neošetřená výjimka pracovního postupu:**    
**System. ApplicationException: Simulovaná chybová podmínka v pracovním postupu.**    
**CancelCreditCard: Zruší poplatky za platební kartu.**    
**Pracovní postup byl úspěšně dokončen se stavem: Zrušil.**  Další informace o zrušení naleznete v tématu [zrušení](modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Explicitní kompenzace pomocí aktivity kompenzace  
 V předchozí části se pokryla implicitní kompenzace. Implicitní kompenzace může být vhodná pro jednoduché scénáře, ale pokud je při plánování zpracování <xref:System.Activities.Statements.Compensate> kompenzace vyžadovánější ovládací prvek, lze aktivitu použít. Chcete-li zahájit proces kompenzace <xref:System.Activities.Statements.Compensate> s aktivitou <xref:System.Activities.Statements.CompensationToken> , <xref:System.Activities.Statements.CompensableActivity> použije se, pro který se náhrada požaduje. Aktivitu lze použít k inicializaci kompenzace u všech dokončených <xref:System.Activities.Statements.CompensableActivity> , které nebyly potvrzeny nebo vyrovnány. <xref:System.Activities.Statements.Compensate> <xref:System.Activities.Statements.Compensate> Aktivitu lze například použít <xref:System.Activities.Statements.TryCatch.Catches%2A> v části <xref:System.Activities.Statements.TryCatch> aktivity nebo kdykoli po jejím <xref:System.Activities.Statements.CompensableActivity> dokončení. V tomto příkladu <xref:System.Activities.Statements.Compensate> se aktivita používá <xref:System.Activities.Statements.TryCatch.Catches%2A> v části <xref:System.Activities.Statements.TryCatch> aktivity k vrácení akce <xref:System.Activities.Statements.CompensableActivity>.  
  
 [!code-csharp[CFX_CompensationExample#3](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 Tento příklad je pracovní postup v jazyce XAML.  
  
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
  
 Po vyvolání pracovního postupu se do konzoly zobrazí následující výstup.  
  
 **ReserveFlight: Lístek je rezervovaný.**  
**SimulatedErrorCondition: Došlo k vyvolání ApplicationException.**    
**CancelFlight: Lístek je zrušený.**    
**Pracovní postup byl úspěšně dokončen se stavem: Ukončit.**    
### <a name="confirming-compensation"></a>Potvrzení kompenzace  
 Ve výchozím nastavení je možné aktivity kompenzovatelná kompenzovat kdykoli po jejich dokončení. V některých případech to nemusí být vhodné. V předchozím příkladu se kompenzace pro rezervaci lístku zrušila. Po dokončení tohoto letu ale tento krok kompenzace už není platný. Potvrzení aktivity kompenzovatelná vyvolá aktivitu určenou v <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>. Jedním z možných použití je umožnit vydání všech prostředků, které jsou nezbytné k vykonání náhrady. Po potvrzení aktivity kompenzovatelná není možné ji kompenzovat a v případě, že se pokusíte o <xref:System.InvalidOperationException> výjimku, je vyvolána výjimka. Po úspěšném dokončení pracovního postupu se všechny nepotvrzené a neuhrazené aktivity kompenzovatelná, které byly úspěšně dokončeny, potvrzují v opačném pořadí dokončení. V tomto příkladu je let rezervovaný, zakoupený a dokončený a pak se potvrdí aktivita kompenzovatelná. Pro potvrzení <xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.CompensationToken> použijte aktivitu a zadejte hodnotu propotvrzení.<xref:System.Activities.Statements.CompensableActivity> <xref:System.Activities.Statements.Confirm>  
  
 [!code-csharp[CFX_CompensationExample#4](~/samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 Tento příklad je pracovní postup v jazyce XAML.  
  
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
  
Po vyvolání pracovního postupu se do konzoly zobrazí následující výstup.  
  
**ReserveFlight: Lístek je rezervovaný.**  
**ManagerApproval: Bylo přijato schválení správcem.**    
**PurchaseFlight: Lístek je koupený.**    
**TakeFlight: Let je dokončený.**    
**ConfirmFlight: Povedlo se ke letu, není možná žádná náhrada.**    
**Pracovní postup byl úspěšně dokončen se stavem: Ukončit.**   

## <a name="nesting-compensation-activities"></a>Vnořování aktivit kompenzace  

Může být umístěn <xref:System.Activities.Statements.CompensableActivity.Body%2A> do části jiného <xref:System.Activities.Statements.CompensableActivity>. <xref:System.Activities.Statements.CompensableActivity> Nesmí být umístěn do obslužné rutiny jiného <xref:System.Activities.Statements.CompensableActivity>typu. <xref:System.Activities.Statements.CompensableActivity> Je zodpovědností nadřazené položky <xref:System.Activities.Statements.CompensableActivity> , aby se zajistilo, že když se zruší, potvrdí nebo kompenzuje všechny podřízené aktivity kompenzovatelná, které byly úspěšně dokončeny a ještě nebyly potvrzeny nebo vyrovnány, musí být potvrzeny nebo náhrada před dokončením zrušení, potvrzení nebo kompenzace nadřazeného objektu. Pokud se nejedná o explicitní modelování, nadřazený <xref:System.Activities.Statements.CompensableActivity> objekt implicitně kompenzuje podřízené aktivity kompenzovatelná, pokud nadřazený objekt obdržel signál pro zrušení nebo kompenzaci. Pokud nadřazená položka obdržela potvrzující signál, Nadřazená aktivita bude implicitně potvrzovat podřízené aktivity kompenzovatelná. Pokud je logika zpracování zrušení, potvrzení nebo kompenzace explicitně modelována v obslužné rutině nadřazené položky <xref:System.Activities.Statements.CompensableActivity>, všechny podřízené objekty, které explicitně nezpracovává, budou implicitně potvrzeny.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Statements.CompensableActivity>
- <xref:System.Activities.Statements.Compensate>
- <xref:System.Activities.Statements.Confirm>
- <xref:System.Activities.Statements.CompensationToken>

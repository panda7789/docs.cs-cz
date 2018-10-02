---
title: Kompenzace
ms.date: 03/30/2017
ms.assetid: 722e9766-48d7-456c-9496-d7c5c8f0fa76
ms.openlocfilehash: 840730acd9289fd394906c49186846e3204c4a99
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863465"
---
# <a name="compensation"></a>Kompenzace
Kompenzace ve Windows Workflow Foundation (WF) je mechanismus, pomocí kterého dříve Dokončená práce vrátit zpět nebo kompenzována (následující logiky definované aplikací.) dojde k následující chybě. Tato část popisuje, jak použít náhradu v pracovních postupech.  
  
## <a name="compensation-vs-transactions"></a>Kompenzace vs. Transakce  
 Transakce můžete zkombinovat několik operací do jedné jednotky práce. Vaše aplikace pomocí transakce dává možnost zrušit všechny změny, které se spustí z v rámci transakce, pokud dojde k nějaké chybě během jakékoli části procesu transakce (vrácení zpět). Použití transakcí však nemusí být vhodné v případě, že je spuštěna po dlouhou dobu práce. Například plánování cestovní aplikace je implementovaný jako pracovní postup. Rezervace letenky, čeká na schválení správce a pak platíte za letu může obsahovat kroky pracovního postupu. Tento proces může trvat dlouho a není praktické kroky rezervace a platit za pochodu k účasti v rámci jedné transakce. Ve scénáři takovou situaci kompenzace může vrátit zpět rezervaci kroku pracovního postupu, pokud dojde k selhání později při zpracování.  
  
> [!NOTE]
>  Toto téma popisuje kompenzace v pracovních postupech. Další informace o transakcích v pracovních postupech najdete v tématu [transakce](../../../docs/framework/windows-workflow-foundation/workflow-transactions.md) a <xref:System.Activities.Statements.TransactionScope>. Další informace o transakcích najdete v tématu <xref:System.Transactions?displayProperty=nameWithType> a <xref:System.Transactions.Transaction?displayProperty=nameWithType>.  
  
## <a name="using-compensableactivity"></a>Aktivita CompensableActivity pomocí  
 <xref:System.Activities.Statements.CompensableActivity> aktivitu kompenzace jader v [!INCLUDE[wf1](../../../includes/wf1-md.md)]. Všechny aktivity, které vykonávají práci, která možná bude nutné kompenzována se umístí do <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity>. V tomto příkladu je krok rezervace letenky nákupu umístí do <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> a zrušení rezervace se umístí do <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>. Přímo za <xref:System.Activities.Statements.CompensableActivity> v pracovním postupu jsou dvě aktivity, které čekání na schválení správce a pak dokončete nákupní krok letu. Pokud chybová podmínka způsobí, že pracovní postup zruší po <xref:System.Activities.Statements.CompensableActivity> bylo úspěšně dokončeno, pak aktivity v <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> obslužné rutiny jsou naplánovány a letu se zruší.  
  
 [!code-csharp[CFX_CompensationExample#1](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#1)]  
  
 V následujícím příkladu je pracovní postup v XAML.  
  
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
  
 Když uživatel vyvolá pracovní postup, se zobrazí následující výstup do konzoly.  
  
 **ReserveFlight: Lístku je vyhrazená.**  
**ManagerApproval: Schválení správcem přijaté.**   
**PurchaseFlight: Lístek jste si koupili.**   
**Pracovního postupu byla úspěšně dokončena se stavem: uzavřeno.**    
> [!NOTE]
>  Ukázkové aktivity v tomto tématu, jako `ReserveFlight` konzolu tak, aby usnadnily pořadí, ve kterém jsou spouštěny aktivity, když dojde k vyrovnání zobrazí jejich název a účel.  
  
### <a name="default-workflow-compensation"></a>Výchozí kompenzace pracovního postupu  
 Ve výchozím nastavení Pokud dojde ke zrušení pracovního postupu, kompenzační logiky se spouští pro jakékoli kompenzovatelná aktivita, která má úspěšně úplně a ještě není potvrzena nebo kompenzována.  
  
> [!NOTE]
>  Když <xref:System.Activities.Statements.CompensableActivity> je *potvrzen*, už může být vyvolána kompenzace aktivity. Procesu potvrzení najdete dál v této části.  
  
 V tomto příkladu je vyvolána výjimka po vyhrazené letu, ale před krokem schválení správce.  
  
 [!code-csharp[CFX_CompensationExample#2](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#2)]  
  
 V tomto příkladu je pracovní postup v XAML.  
  
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
  
 Když uživatel vyvolá pracovní postup, je simulované chybě podmínku výjimka ošetřena hostitele aplikací v <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, pracovní postup zrušení a je vyvolána kompenzační logiky.  
  
 **ReserveFlight: Lístku je vyhrazená.**  
**SimulatedErrorCondition: Došlo ApplicationException.**   
**Pracovní postup neošetřená výjimka:**   
**System.ApplicationException: Simulované chybě v pracovním postupu.**   
**CancelFlight: Lístek se zrušila.**   
**Pracovního postupu byla úspěšně dokončena se stavem: bylo zrušeno.**    
### <a name="cancellation-and-compensableactivity"></a>Zrušení a aktivita CompensableActivity  
 Pokud aktivity v <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> mají nedokončený a aktivity se zruší, aktivity v <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> provádějí.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Je vyvolána pouze v případě aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> nedokončili a aktivity se zruší. <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A> Se provede pouze, pokud aktivity <xref:System.Activities.Statements.CompensableActivity.Body%2A> z <xref:System.Activities.Statements.CompensableActivity> úspěšně dokončit a kompenzace je následně volána v aktivitě.  
  
 <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> Dává příležitost k poskytování logiky pro všechny příslušné zrušení autoři pracovního postupu. V následujícím příkladu, dojde k výjimce během zpracování <xref:System.Activities.Statements.CompensableActivity.Body%2A>a pak <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> je vyvolána.  
  
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
  
 V tomto příkladu je pracovní postup v XAML  
  
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
  
 Když uživatel vyvolá pracovní postup, je simulované chybě podmínku výjimka ošetřena hostitele aplikací v <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>, dojde ke zrušení pracovního postupu a logiku zrušení <xref:System.Activities.Statements.CompensableActivity> je vyvolána. V tomto příkladu kompenzační logika a logika zrušení mají různé cíle. Pokud <xref:System.Activities.Statements.CompensableActivity.Body%2A> se nedokončil úspěšně, pak to znamená platební karty se naúčtovala platba a si letu, takže vyrovnání by měl vrátit zpět oba kroky. (V tomto příkladu ruší letu se automaticky zruší poplatky platební karty.) Ale pokud <xref:System.Activities.Statements.CompensableActivity> dojde ke zrušení, to znamená, že <xref:System.Activities.Statements.CompensableActivity.Body%2A> nebyla úplný a tak logiku <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> musí být schopní určit, jak nejlépe zpracovat zrušení. V tomto příkladu <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> zruší platební kartu poplatek, ale od té doby `ReserveFlight` byl poslední aktivita v <xref:System.Activities.Statements.CompensableActivity.Body%2A>, se nebude pokoušet o zrušení letu. Protože `ReserveFlight` byl poslední aktivita v <xref:System.Activities.Statements.CompensableActivity.Body%2A>, pokud bylo úspěšně dokončeno pak bude <xref:System.Activities.Statements.CompensableActivity.Body%2A> byste dokončili a bez zrušení by bylo možné.  
  
 **ChargeCreditCard: Platby prostřednictvím platební karty pro let.**  
**SimulatedErrorCondition: Došlo ApplicationException.**   
**Pracovní postup neošetřená výjimka:**   
**System.ApplicationException: Simulované chybě v pracovním postupu.**   
**CancelCreditCard: Zrušit platební karty poplatky.**   
**Pracovního postupu byla úspěšně dokončena se stavem: bylo zrušeno.**  Další informace o zrušení naleznete v tématu [zrušení](../../../docs/framework/windows-workflow-foundation/modeling-cancellation-behavior-in-workflows.md).  
  
### <a name="explicit-compensation-using-the-compensate-activity"></a>Pomocí explicitní kompenzaci aktivitu kompenzace  
 V předchozí části zkušebním implicitní kompenzaci. Implicitní kompenzace může být vhodné pro jednoduché scénáře, ale pokud podrobnější je vyžadováno řízení nad plánováním kompenzace pak zpracování <xref:System.Activities.Statements.Compensate> aktivita se dá použít. K zahájení kompenzace s <xref:System.Activities.Statements.Compensate> aktivity, <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> pro které kompenzace je žádoucí se používá. <xref:System.Activities.Statements.Compensate> Aktivita slouží k zahájení kompenzaci na žádném dokončení <xref:System.Activities.Statements.CompensableActivity> , která nebyla potvrzena nebo kompenzována. Například <xref:System.Activities.Statements.Compensate> aktivity se daly použít v <xref:System.Activities.Statements.TryCatch.Catches%2A> část <xref:System.Activities.Statements.TryCatch> aktivity nebo kdykoli po dokončení <xref:System.Activities.Statements.CompensableActivity> byla dokončena. V tomto příkladu <xref:System.Activities.Statements.Compensate> aktivita se používá v <xref:System.Activities.Statements.TryCatch.Catches%2A> část <xref:System.Activities.Statements.TryCatch> aktivitu pro vrácení akce <xref:System.Activities.Statements.CompensableActivity>.  
  
 [!code-csharp[CFX_CompensationExample#3](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#3)]  
  
 V tomto příkladu je pracovní postup v XAML.  
  
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
  
 Když uživatel vyvolá pracovní postup, se zobrazí následující výstup do konzoly.  
  
 **ReserveFlight: Lístku je vyhrazená.**  
**SimulatedErrorCondition: Došlo ApplicationException.**   
**CancelFlight: Lístek se zrušila.**   
**Pracovního postupu byla úspěšně dokončena se stavem: uzavřeno.**    
### <a name="confirming-compensation"></a>Potvrzují se kompenzace  
 Ve výchozím nastavení kompenzovatelné aktivity kompenzovat lze kdykoli po jejich dokončení. V některých případech to nemusí být vhodné. V předchozím příkladu byl kompenzace k rezervaci-the-ticket ke zrušení rezervace. Po dokončení letu tento krok kompenzace je však již platná. Potvrzení kompenzovatelné aktivity volá aktivita určené <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>. Jeden využití pro tuto je umožnit všechny prostředky, které jsou nezbytné k provedení náhrady uvolnit. Jakmile se potvrdí kompenzovatelné aktivity není možné, aby se kompenzována a tím dojde k pokusu o <xref:System.InvalidOperationException> je vyvolána výjimka. Po úspěšném dokončení pracovního postupu, jsou všechny nepotvrzené a kompenzována kompenzovatelné aktivity, které byla úspěšně dokončena v obráceném pořadí potvrdit dokončení. V tomto příkladu je letu vyhrazené, koupit a dokončit, a pak je potvrzen kompenzovatelné aktivity. Potvrďte <xref:System.Activities.Statements.CompensableActivity>, použijte <xref:System.Activities.Statements.Confirm> aktivity a zadejte <xref:System.Activities.Statements.CompensationToken> z <xref:System.Activities.Statements.CompensableActivity> potvrďte.  
  
 [!code-csharp[CFX_CompensationExample#4](../../../samples/snippets/csharp/VS_Snippets_CFX/CFX_CompensationExample/cs/Program.cs#4)]  
  
 V tomto příkladu je pracovní postup v XAML.  
  
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
  
Když uživatel vyvolá pracovní postup, se zobrazí následující výstup do konzoly.  
  
**ReserveFlight: Lístku je vyhrazená.**  
**ManagerApproval: Schválení správcem přijaté.**   
**PurchaseFlight: Lístek jste si koupili.**   
**TakeFlight: Letu je dokončen.**   
**ConfirmFlight: Letu se nestalo, žádné honoráře je to možné.**   
**Pracovního postupu byla úspěšně dokončena se stavem: uzavřeno.**   

## <a name="nesting-compensation-activities"></a>Vnoření kompenzace aktivity  

A <xref:System.Activities.Statements.CompensableActivity> , jde umístit do <xref:System.Activities.Statements.CompensableActivity.Body%2A> části jiného <xref:System.Activities.Statements.CompensableActivity>. A <xref:System.Activities.Statements.CompensableActivity> nelze umístit do rutiny jiného <xref:System.Activities.Statements.CompensableActivity>. Zodpovídá za nadřazeného <xref:System.Activities.Statements.CompensableActivity> zajistit, že pokud je zrušen, potvrzena nebo kompenzována, všechny podřízené kompenzovatelné aktivity, které byly úspěšně dokončeny a ještě není byla potvrzena nebo kompenzována musí být potvrzeny nebo kompenzována předtím, než nadřazená dokončení zrušení, confirmation nebo kompenzaci. Pokud to není explicitně modelovat nadřazené <xref:System.Activities.Statements.CompensableActivity> bude implicitně kompenzace podřízené kompenzovatelné aktivity, pokud nadřazená dostali zrušení nebo kompenzaci signálu. Pokud nadřazená přijal signál potvrzení nadřazené potvrdí implicitně podřízené kompenzovatelné aktivity. Pokud logiku ke zpracování zrušení, confirmation nebo kompenzace je explicitně modelován v obslužné rutině nadřazené <xref:System.Activities.Statements.CompensableActivity>, všech podřízených nejsou explicitně zpracována bude implicitně potvrzen.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Activities.Statements.CompensableActivity>  
- <xref:System.Activities.Statements.Compensate>  
- <xref:System.Activities.Statements.Confirm>  
- <xref:System.Activities.Statements.CompensationToken>
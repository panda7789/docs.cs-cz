---
title: "Vytváření pracovních postupů, aktivity a výrazy pomocí imperativní kódu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1cdc4327c38de16e8ff472001622f3b25e0fe6f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>Vytváření pracovních postupů, aktivity a výrazy pomocí imperativní kódu
Definice pracovního postupu je strom objektů nakonfigurované aktivity. Tento strom aktivity může být definováno mnoha způsoby, třeba pomocí ruční úpravě XAML nebo pomocí návrháře pracovních postupů k vytvoření XAML. Použití jazyka XAML, ale není požadavek. Definice pracovního postupu můžete vytvořit také prostřednictvím kódu programu. Toto téma obsahuje přehled vytvoření definice pracovního postupu, aktivity a výrazy pomocí kódu. Příklady práci s pracovními postupy XAML pomocí kódu najdete v tématu [serializaci pracovních postupů a aktivit do a z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
## <a name="creating-workflow-definitions"></a>Vytvoření definice pracovního postupu  
 Definice pracovního postupu můžete vytvořit pomocí vytvoření instance instanci typu aktivity a vlastnosti aktivity objektu konfigurace. Pro aktivity, které neobsahují podřízené aktivity můžete to provést pomocí několika řádků kódu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
>  V příkladech v tomto tématu <xref:System.Activities.WorkflowInvoker> ke spouštění pracovních postupů ukázka. [!INCLUDE[crabout](../../../includes/crabout-md.md)]vyvolání pracovní postupy, předávání argumentů a různé hostování možnosti, které jsou k dispozici, najdete v části [pomocí WorkflowInvoker a WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md).  
  
 V tomto příkladu, pracovní postup, který se skládá z jedné <xref:System.Activities.Statements.WriteLine> vytvoření aktivity. <xref:System.Activities.Statements.WriteLine> Aktivity <xref:System.Activities.Statements.WriteLine.Text%2A> argument je nastaven, a je volána pracovního postupu. Pokud aktivita obsahuje podřízené aktivity, je podobný metodu konstrukce. Následující příklad používá <xref:System.Activities.Statements.Sequence> aktivity, která obsahuje dva <xref:System.Activities.Statements.WriteLine> aktivity.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>Pomocí inicializátory objektů  
 V příkladech v tomto tématu použijte syntaxi inicializace objektu. Syntaxe inicializace objektu může být užitečný způsob, jak vytvořit definice pracovního postupu v kódu, protože poskytuje hierarchické zobrazení aktivity v pracovním postupu a znázorňuje vztah mezi aktivitami. Neexistuje žádný požadavek na použití syntaxe inicializace objektu při prostřednictvím kódu programu vytváření pracovních postupů. V následujícím příkladu je funkčně srovnatelný předchozí příklad.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Inicializátory objektu, najdete v části [postup: inicializovat objekty bez volání konstruktoru (C# Průvodce programováním)](http://go.microsoft.com/fwlink/?LinkId=161015) a [postupy: Deklarace objektu pomocí inicializátoru objektu](http://go.microsoft.com/fwlink/?LinkId=161016).  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>Práce s proměnnými, literálových hodnot a výrazů  
 Při vytváření definice pracovního postupu pomocí kódu, zajímat, jaký kód spustí jako součást vytvoření definice pracovního postupu a jaký kód spustí jako součást spuštění instance pracovního postupu. Například následující pracovní postup slouží ke generování náhodné číslo a zapisuje do konzoly.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 Při spuštění tohoto kódu definice pracovního postupu, volání `Random.Next` přišla a výsledek je uložen v definici pracovního postupu jako hodnota literálu. Počet instancí tento pracovní postup může vyvolat, a všechny by zobrazit stejné číslo. Tak, aby měl náhodné generování čísel, ke kterým došlo během provádění pracovního postupu, který je použit výraz vyhodnocovány pokaždé, když pracovní postup bude spuštěn. V následujícím příkladu je použit výraz jazyka Visual Basic s <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Výraz v předchozím příkladu lze také implementovat pomocí <xref:Microsoft.CSharp.Activities.CSharpValue%601> a výraz jazyka C#.  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 Výrazy jazyka C# musí být zkompilovány, před vyvoláním pracovního postupu, které je obsahují. Pokud nejsou kompilovány výrazy jazyka C#, <xref:System.NotSupportedException> se vyvolá, když pracovní postup vyvolání zpráva podobná následující: `Expression Activity type 'CSharpValue`1 vyžaduje kompilace aby bylo možné spustit.  Zkontrolujte, že pracovní postup byl zkompilován.' ve většině scénářů zahrnující pracovní postupy vytvořené v sadě Visual Studio jazyka C# jsou výrazy automaticky kompilovat, ale v některých případech, například kód pracovních postupů, musí výrazy jazyka C# ručně kompilována. Příklad způsob kompilace výrazy jazyka C#, naleznete v části [pomocí jazyka C# výrazy v pracovních postupech kódu](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) části [výrazy jazyka C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md) tématu.  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> představuje výraz v syntaxi jazyka Visual Basic, který lze použít jako r-value ve výrazu a <xref:Microsoft.CSharp.Activities.CSharpValue%601> představuje výraz v syntaxi C#, který lze použít jako r-value ve výrazu. Tyto výrazy jsou vyhodnocovány pokaždé, když se spustí obsahující aktivitu. Výsledkem výrazu je přiřazen k proměnné pracovního postupu `n`, a tyto výsledky jsou používány na další aktivitu v pracovním postupu. Pro přístup k hodnotě proměnné pracovního postupu `n` v době běhu <xref:System.Activities.ActivityContext> je vyžadován. To je přístupná pomocí následující výrazu lambda.  
  
> [!NOTE]
>  Všimněte si, že jsou obě tyto kódu příklady použití jazyka C# jako programovací jazyk, ale jedna používá <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> a jeden používá <xref:Microsoft.CSharp.Activities.CSharpValue%601>. <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>a <xref:Microsoft.CSharp.Activities.CSharpValue%601> lze použít v projektech Visual Basic a C#. Ve výchozím nastavení výrazy, které jsou vytvořené v Návrháři pracovních postupů s jazykem hostování projektu. Při vytváření pracovních postupů v kódu, požadovaný jazyk je uvážení Autor pracovního postupu.  
  
 V těchto příkladech je výsledkem výrazu přiřazenou proměnné pracovního postupu `n`, a tyto výsledky jsou používány na další aktivitu v pracovním postupu. Pro přístup k hodnotě proměnné pracovního postupu `n` v době běhu <xref:System.Activities.ActivityContext> je vyžadován. To je přístupná pomocí následující výrazu lambda.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]lambda – výrazy, najdete v části [výrazy Lambda (C# Průvodce programováním)](http://go.microsoft.com/fwlink/?LinkID=152436) nebo [výrazy Lambda (Visual Basic)](http://go.microsoft.com/fwlink/?LinkID=152437).  
  
 Lambda – výrazy nejsou serializovatelný do formátu XAML. Pokud se pokus o serializaci pracovního postupu s výrazy lambda, <xref:System.Activities.Expressions.LambdaSerializationException> je vyvolána s následující zprávou: "Tento pracovní postup obsahuje výrazy lambda zadaný v kódu. Tyto výrazy nejsou XAML serializable. Aby bylo možné serializovatelný XAML pracovního postupu, použijte buď VisualBasicValue/VisualBasicReference nebo ExpressionServices.Convert(lambda). To bude vaše výrazy lambda výraz aktivity převést." Chcete-li tento výraz kompatibilní s XAML, použijte <xref:System.Activities.Expressions.ExpressionServices> a <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> může také použít. Všimněte si, že žádný výraz lambda je potřeba při použití výraz jazyka Visual Basic.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 V době běhu jsou výrazy jazyka Visual Basic zkompilovat do LINQ – výrazy. V předchozích příkladech jsou serializovatelný do jazyka XAML, ale pokud serializovaných XAML slouží jako prohlížet a upravovat v Návrháři pracovních postupů pomocí <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> pro vaše výrazy. Pracovní postupy, které používají serializovat `ExpressionServices.Convert` lze otevřít v návrháři, ale hodnota výrazu bude prázdné. [!INCLUDE[crabout](../../../includes/crabout-md.md)]serializace pracovní postupy pro XAML, najdete v části [serializaci pracovních postupů a aktivit do a z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
#### <a name="literal-expressions-and-reference-types"></a>Literál výrazy a odkazové typy  
 Literálové výrazy jsou reprezentována v pracovních postupech, pomocí <xref:System.Activities.Expressions.Literal%601> aktivity. Následující <xref:System.Activities.Statements.WriteLine> aktivity jsou funkčně rovnocenné.  
  
```csharp  
new WriteLine  
{  
    Text = "Hello World."  
},  
new WriteLine  
{  
    Text = new Literal<string>("Hello World.")  
}  
```  
  
 Je neplatné. k chybě při inicializaci literál výrazu s žádným typem odkaz s výjimkou <xref:System.String>. V následujícím příkladu se <xref:System.Activities.Statements.Assign> aktivity <xref:System.Activities.Statements.Assign.Value%2A> vlastnost je inicializována pomocí literál výrazu `List<string>`.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 Když je pracovní postup obsahující této aktivity ověřit, se vrátí následující chybu ověřování: "literál podporuje pouze typy hodnot a typ neměnné System.String. Typ System.Collections.Generic.List'1[System.String] nelze použít jako literál." Pokud je pracovní postup je vyvolána, <xref:System.Activities.InvalidWorkflowException> je vyvolána obsahující text chyby ověření. Jedná se o chybu ověření, protože vytváření literál výrazu s odkazového typu nevytvoří novou instanci třídy typ odkazu pro každou instanci pracovního postupu. To vyřešit, nahraďte literál výrazu, která vytvoří a vrátí novou instanci typu odkazu.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]výrazy, najdete v části [výrazy](../../../docs/framework/windows-workflow-foundation/expressions.md).  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>Volání metod pro objekty pomocí výrazy a InvokeMethod aktivity  
 <xref:System.Activities.Expressions.InvokeMethod%601> Aktivity slouží k vyvolání statické a instance metody třídy v rozhraní .NET Framework. V předchozím příkladu v tomto tématu se generuje náhodné číslo, pomocí <xref:System.Random> třídy.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 <xref:System.Activities.Expressions.InvokeMethod%601> Aktivity také byl použit k volání <xref:System.Random.Next%2A> metodu <xref:System.Random> třídy.  
  
```csharp  
new InvokeMethod<int>  
{  
    TargetObject = new InArgument<Random>(new VisualBasicValue<Random>("New Random()")),  
    MethodName = "Next",  
    Parameters =   
    {  
        new InArgument<int>(1),  
        new InArgument<int>(101)  
    },  
    Result = n  
}  
```  
  
 Vzhledem k tomu <xref:System.Random.Next%2A> není statickou metodu, instanci <xref:System.Random> třída poskytnutý <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> vlastnost. V tomto příkladu je vytvořena nová instance pomocí výrazu jazyka Visual Basic, ale může také mít byla dříve vytvořili a uložené v proměnné pracovního postupu. V tomto příkladu je jednodušší použít <xref:System.Activities.Statements.Assign%601> aktivity místo <xref:System.Activities.Expressions.InvokeMethod%601> aktivity. Pokud volání metody nakonec vyvolat buď <xref:System.Activities.Statements.Assign%601> nebo <xref:System.Activities.Expressions.InvokeMethod%601> aktivit je dlouho spuštěný, <xref:System.Activities.Expressions.InvokeMethod%601> má několik výhod, protože má <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> vlastnost. Pokud je tato vlastnost nastavená na `true`, vyvolanou metodu se spustí asynchronně s ohledem na pracovním postupu. Pokud ostatní aktivity paralelně, nebude při asynchronně spouští metodu blokován. Navíc pokud metoda k vyvolání nemá žádnou návratovou hodnotu, pak <xref:System.Activities.Expressions.InvokeMethod%601> je vhodný způsob k vyvolání metody.  
  
## <a name="arguments-and-dynamic-activities"></a>Argumenty a dynamické aktivity  
 Definice pracovního postupu se vytvoří v kódu ty aktivity do strom aktivity a konfigurací všechny vlastnosti a argumenty. Mohou být vázány existující argumenty, ale nové argumenty nelze přidat do aktivity. To zahrnuje předána aktivitě, kořenové argumenty pracovního postupu. V imperativní kódu jsou zadané argumenty pracovního postupu jako vlastnosti na nový typ CLR, a v jazyce XAML jsou deklarovány s použitím `x:Class` a `x:Member`. Argumenty nelze přidat, protože neexistuje žádný nový typ CLR vytvořit při vytváření definice pracovního postupu jako strom objektů v paměti. Argumenty by však mohou být přidány do <xref:System.Activities.DynamicActivity>. V tomto příkladu <xref:System.Activities.DynamicActivity%601> se vytvoří dva argumenty celé číslo tohoto trvá, společně se přidají a vrátí výsledek. A <xref:System.Activities.DynamicActivityProperty> se vytvoří pro každý argument a výsledek operace je přiřazena k <xref:System.Activities.Activity%601.Result%2A> argument <xref:System.Activities.DynamicActivity%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]dynamické aktivity, najdete v části [vytváření aktivitu v době běhu](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md).  
  
## <a name="compiled-activities"></a>Kompilované aktivity  
 Dynamické aktivity jsou jeden způsob, jak definovat aktivity, která obsahuje argumenty pomocí kódu, ale aktivity také můžete vytvořit v kódu a zkompilovat do typy. Které jsou odvozeny od vytvořením jednoduchého aktivity <xref:System.Activities.CodeActivity>a asynchronní aktivity, které jsou odvozeny od <xref:System.Activities.AsyncCodeActivity>. Tyto aktivity může mít argumenty, návratové hodnoty a definovat jejich logiku pomocí imperativní kódu. Příklady vytváření tyto typy aktivit najdete v tématu [CodeActivity základní třída](../../../docs/framework/windows-workflow-foundation/workflow-activity-authoring-using-the-codeactivity-class.md) a [vytváření asynchronní aktivity](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
 Aktivity, které jsou odvozeny od <xref:System.Activities.NativeActivity> můžete definovat jejich logiku pomocí imperativní kódu a může také obsahovat podřízené aktivity, které definují logiku. Také mají plný přístup k funkcím runtime, jako je například vytváření záložky. Příklady vytváření <xref:System.Activities.NativeActivity>– na základě aktivity, najdete v části [NativeActivity základní třída](../../../docs/framework/windows-workflow-foundation/nativeactivity-base-class.md), [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)a [vlastní složený pomocí nativní aktivity](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-using-native-activity.md)ukázka.  
  
 Aktivity, které jsou odvozeny od <xref:System.Activities.Activity> definovat jejich logiku výhradně prostřednictvím podřízené aktivity. Tyto aktivity jsou obvykle vytvoří pomocí návrháře pracovních postupů, ale lze také definovat pomocí kódu. V následujícím příkladu `Square` aktivity je definována odvozenou od `Activity<int>`. `Square` Aktivita má jeden <xref:System.Activities.InArgument%601> s názvem `Value`a definuje svou logikou zadáním <xref:System.Activities.Statements.Sequence> aktivity pomocí <xref:System.Activities.Activity.Implementation%2A> vlastnost. <xref:System.Activities.Statements.Sequence> Obsahuje aktivitu <xref:System.Activities.Statements.WriteLine> aktivity a <xref:System.Activities.Statements.Assign%601> aktivity. Společně tyto tři aktivity implementovat logiku `Square` aktivity.  
  
```csharp  
class Square : Activity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Value { get; set; }  
  
    public Square()  
    {  
        this.Implementation = () => new Sequence  
        {  
            Activities =  
            {  
                new WriteLine  
                {  
                    Text = new InArgument<string>((env) => "Squaring the value: " + this.Value.Get(env))  
                },  
                new Assign<int>  
                {  
                    To = new OutArgument<int>((env) => this.Result.Get(env)),  
                    Value = new InArgument<int>((env) => this.Value.Get(env) * this.Value.Get(env))  
                }  
            }  
        };  
    }  
}  
```  
  
 V následujícím příkladu, definice pracovního postupu, který se skládá z jedné `Square` aktivity vyvolání pomocí <xref:System.Activities.WorkflowInvoker>.  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 Po vyvolání pracovního postupu se ke konzole zobrazí následující výstup:  
  
 **Umocněním hodnota: 5**  
**Výsledek: 25**

---
title: Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu
ms.date: 03/30/2017
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
ms.openlocfilehash: a0566e01d5786c955562ef97d6d083d886278293
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44061452"
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu
Definice pracovního postupu je strom objektů nakonfigurované aktivity. Tento strom aktivity mohou být definovány mnoha způsoby, třeba pomocí ruční úpravy XAML nebo vytvořit XAML pomocí návrháře postupu provádění. Použití XAML, ale není povinné. Definice pracovního postupu můžete vytvořit také prostřednictvím kódu programu. Toto téma obsahuje přehled o vytvoření definice pracovních postupů, aktivit a výrazů s použitím kódu. Příklady práce s pracovními postupy XAML pomocí kódu, naleznete v tématu [serializace pracovních postupů a aktivit do a z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
## <a name="creating-workflow-definitions"></a>Vytváří se definice pracovního postupu  
 Vytvoření instance typu aktivity a nastavením vlastnosti objektu aktivity lze vytvořit definici pracovního postupu. Pro aktivity, které neobsahují podřízené aktivity můžete to provést pomocí několika řádků kódu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
>  V příkladech v tomto tématu využívají <xref:System.Activities.WorkflowInvoker> ke spouštění pracovních postupů vzorku. Další informace o pracovních postupů a předávání argumentů a hostingové možnosti, které jsou k dispozici, najdete v části [použití WorkflowInvoker a WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md).  
  
 V tomto příkladu, pracovní postup, který se skládá z jedné <xref:System.Activities.Statements.WriteLine> vytvoření aktivity. <xref:System.Activities.Statements.WriteLine> Aktivity <xref:System.Activities.Statements.WriteLine.Text%2A> argument je nastaven, a vyvolá pracovní postup. Pokud aktivita obsahuje podřízené aktivity, metoda konstrukce podobná. Následující příklad používá <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje dva <xref:System.Activities.Statements.WriteLine> aktivity.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>Inicializátory objektů pomocí  
 Příklady v tomto tématu pomocí syntaxe inicializace objektu. Syntaxe inicializace objektu může být užitečný způsob, jak vytvořit definice pracovního postupu v kódu, protože obsahuje hierarchické zobrazení aktivity v pracovním postupu a znázorňuje vztah mezi aktivitami. Neexistuje žádný požadavek na pomocí syntaxe inicializace objektu při programově vytvářet pracovní postupy. Následující příklad je funkčně srovnatelný s předchozím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 Další informace o inicializátory objektů najdete v tématu [jak: Inicializace objektů bez volání konstruktoru (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkId=161015) a [postupy: Deklarace objektu pomocí inicializátoru objektu](https://go.microsoft.com/fwlink/?LinkId=161016).  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>Práce s proměnnými, literálové hodnoty a výrazy  
 Při vytváření definice pracovního postupu pomocí kódu, mějte na paměti jaký kód provede jako součást vytváření definice pracovního postupu a jaký kód provede jako součást spuštění instance pracovního postupu. Například následující pracovní postup má generovat náhodné číslo a zápis do konzoly.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 Při spuštění tohoto kódu pro definici pracovního postupu, volání `Random.Next` tvoří a výsledek je uložen v definici pracovního postupu jako hodnotu literálu. Velký počet instancí tento pracovní postup může být vyvolána, a všechny zobrazí stejné číslo. Aby generování náhodných čísel, k nimž došlo při provádění pracovního postupu, který je použit výraz vyhodnocen pokaždé, když pracovní postup probíhá. V následujícím příkladu se používá výraz jazyka Visual Basic s <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Výraz v předchozím příkladu může implementovat také pomocí <xref:Microsoft.CSharp.Activities.CSharpValue%601> a výraz C#.  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 Výrazy jazyka C# musí být zkompilovány před vyvoláním pracovního postupu, které je obsahují. Pokud nejsou výrazy jazyka C# zkompilovány, <xref:System.NotSupportedException> je vyvolána, když uživatel vyvolá pracovní postup a zobrazí se zpráva podobná této: `Expression Activity type 'CSharpValue`1 vyžaduje kompilaci, aby bylo možné spustit.  Ujistěte se prosím, že pracovní postup byl zkompilován. "ve většině případů zahrnující pracovní postupy vytvořené v sadě Visual Studio C# výrazy jsou zkompilovány automaticky, ale v některých scénářích, jako jsou pracovní postupy kódu výrazy jazyka C# musí být ručně kompilována. Příklad zkompilovat výrazy jazyka C# najdete v článku [výrazy pomocí jazyka C# v pracovních postupech kód](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) část [výrazy jazyka C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md) tématu.  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> představuje výraz v syntaxi jazyka Visual Basic, který může sloužit jako r-value ve výrazu, a <xref:Microsoft.CSharp.Activities.CSharpValue%601> představuje výraz v syntaxi jazyka C#, který může sloužit jako r-value ve výrazu. Tyto výrazy jsou vyhodnocovány pokaždé, když je proveden obsahující aktivitu. Výsledek výrazu je přiřazená k proměnné pracovního postupu `n`, a tyto výsledky se používají další aktivita v pracovním postupu. Pro přístup k hodnotě proměnné pracovního postupu `n` v době běhu <xref:System.Activities.ActivityContext> je povinný. To lze přistupovat pomocí následující výraz lambda.  
  
> [!NOTE]
>  Všimněte si, že jsou obě tyto kód příklady jsou pomocí jazyka C# jako programovací jazyk, ale jeden používá <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> a jedna používá <xref:Microsoft.CSharp.Activities.CSharpValue%601>. <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> a <xref:Microsoft.CSharp.Activities.CSharpValue%601> lze použít v projektech Visual Basic a C#. Ve výchozím nastavení výrazy vytvořené v Návrháři postupu provádění jazyk hostování projektu. Při vytváření pracovních postupů v kódu, požadovaný jazyk je uvážení Autor pracovního postupu.  
  
 V těchto příkladech výsledek výrazu je přiřazen k proměnné pracovního postupu `n`, a tyto výsledky se používají další aktivita v pracovním postupu. Pro přístup k hodnotě proměnné pracovního postupu `n` v době běhu <xref:System.Activities.ActivityContext> je povinný. To lze přistupovat pomocí následující výraz lambda.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 Další informace o výrazech lambda naleznete v tématu [výrazy Lambda (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkID=152436) nebo [výrazy Lambda (Visual Basic)](https://go.microsoft.com/fwlink/?LinkID=152437).  
  
 Výrazy lambda nejsou serializovat do formátu XAML. Pokud je proveden pokus o serializaci pracovního postupu pomocí výrazů lambda, <xref:System.Activities.Expressions.LambdaSerializationException> je vyvolána výjimka s následující zprávou: "Tento pracovní postup obsahuje výrazy lambda určené v kódu. Tyto výrazy nejsou XAML serializovatelný. Aby bylo možné serializovat XAML pracovního postupu, použijte funkce VisualBasicValue/VisualBasicReference nebo ExpressionServices.Convert(lambda). To převede převedete výrazy lambda na aktivity výrazů." Chcete-li tento výraz kompatibilní s XAML, použijte <xref:System.Activities.Expressions.ExpressionServices> a <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> může také použít. Všimněte si, že žádný výraz lambda je povinný při použití výraz jazyka Visual Basic.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 V době běhu jsou výrazy jazyka Visual Basic kompilovány do LINQ – výrazy. V předchozích příkladech jsou serializovatelné XAML, ale pokud serializovaná XAML se má zobrazit a upravit v Návrháři pracovních postupů pomocí <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> pro vaše výrazy. Pracovní postupy využívající serializovat `ExpressionServices.Convert` lze otevřít v návrháři, ale hodnota výrazu bude prázdné. Další informace o serializaci pracovní postupy XAML najdete v tématu [serializace pracovních postupů a aktivit do a z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
#### <a name="literal-expressions-and-reference-types"></a>Literálové výrazy a odkazové typy  
 Literálové výrazy jsou reprezentovány v pracovních postupech podle <xref:System.Activities.Expressions.Literal%601> aktivity. Následující <xref:System.Activities.Statements.WriteLine> aktivity jsou funkčně ekvivalentní.  
  
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
  
 Je neplatná inicializace literálový výraz s jakéhokoliv odkazového typu s výjimkou <xref:System.String>. V následujícím příkladu <xref:System.Activities.Statements.Assign> aktivity <xref:System.Activities.Statements.Assign.Value%2A> vlastnost je inicializována pomocí literálový výraz `List<string>`.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 Po ověření pracovního postupu, který obsahuje tato aktivita se vrátí následující chybu ověření: "literál podporuje typy hodnot a je neumlčitelným typem System.String. Typ System.Collections.Generic.List'1[System.String] nelze použít jako literál." Pokud je vyvolána pracovního postupu, <xref:System.Activities.InvalidWorkflowException> je vyvolána výjimka, která obsahuje text chyby ověření. Jedná se o chybu ověření, protože vytváření literálový výraz s odkazovým typem nevytvoří novou instanci typu odkazu pro každou instanci pracovního postupu. Chcete-li tento problém vyřešit, nahraďte literálový výraz ten, který vytvoří a vrátí novou instanci typu odkazu.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 Další informace o výrazech naleznete v tématu [výrazy](../../../docs/framework/windows-workflow-foundation/expressions.md).  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>Volání metod na objekty pomocí výrazů a aktivity InvokeMethod  
 <xref:System.Activities.Expressions.InvokeMethod%601> Aktivita slouží pro vyvolání statické a instance metod tříd v rozhraní .NET Framework. V předchozím příkladu v tomto tématu se vygeneroval pomocí náhodné číslo <xref:System.Random> třídy.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 <xref:System.Activities.Expressions.InvokeMethod%601> Aktivita může také byla použita k volání <xref:System.Random.Next%2A> metodu <xref:System.Random> třídy.  
  
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
  
 Protože <xref:System.Random.Next%2A> není statická metoda instance <xref:System.Random> třídy poskytnutý <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> vlastnost. V tomto příkladu je vytvořena nová instance pomocí výraz jazyka Visual Basic, ale může také mít byla předtím vytvořili a uloží do proměnné pracovního postupu. V tomto příkladu je jednodušší použít <xref:System.Activities.Statements.Assign%601> aktivity místo <xref:System.Activities.Expressions.InvokeMethod%601> aktivity. Pokud volání metody, které nakonec vyvolávat buď <xref:System.Activities.Statements.Assign%601> nebo <xref:System.Activities.Expressions.InvokeMethod%601> aktivit je dlouhý spuštěna, <xref:System.Activities.Expressions.InvokeMethod%601> je výhodné, protože má <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> vlastnost. Pokud je tato vlastnost nastavena na `true`, jde o pracovní postup spustí asynchronně volanou metodu. Pokud jiné aktivity paralelně, nebude blokován při se metoda provádí asynchronně. Také pokud metoda k vyvolání nemá žádnou návratovou hodnotu, pak <xref:System.Activities.Expressions.InvokeMethod%601> je vhodný způsob volání metody.  
  
## <a name="arguments-and-dynamic-activities"></a>Argumenty a dynamické aktivity  
 Definice pracovního postupu se vytvoří v kódu propojením aktivit na strom aktivity a konfigurací vlastností a argumenty. Existující argumenty může být vázaný, ale nové argumenty nelze přidat do aktivity. To zahrnuje pracovní postup argumenty předané kořenovou aktivitu. V imperativního kódu jsou zadané argumenty pracovního postupu jako vlastnosti na nový typ CLR, a v XAML jsou deklarovány pomocí `x:Class` a `x:Member`. Argumenty nelze přidat, protože neexistuje žádný nový typ CLR vytvořený při vytváření definice pracovního postupu jako strom objektů v paměti. Argumenty ale mohou být přidány do <xref:System.Activities.DynamicActivity>. V tomto příkladu <xref:System.Activities.DynamicActivity%601> vytvoření této přebírá dva celočíselné argumenty, se přidají společně a vrátí výsledek. A <xref:System.Activities.DynamicActivityProperty> se vytvoří pro každý argument a výsledkem operace je přiřazen k <xref:System.Activities.Activity%601.Result%2A> argument <xref:System.Activities.DynamicActivity%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 Další informace o dynamické aktivity najdete v tématu [vytvoření aktivity za běhu](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md).  
  
## <a name="compiled-activities"></a>Kompilované aktivity  
 Dynamické aktivity jsou jeden způsob, jak definovat aktivity, která obsahuje argumenty pomocí kódu, ale můžete aktivity také vytvoří v kódu a zkompilovány do typů. Jednoduché lze vytvořit aktivity, které jsou odvozeny z <xref:System.Activities.CodeActivity>a asynchronních aktivitách, které jsou odvozeny z <xref:System.Activities.AsyncCodeActivity>. Tyto aktivity mohou mít argumenty, návratové hodnoty a definovat jeho logiku pomocí imperativního kódu. Příklady vytváření těchto druhů aktivit najdete v tématu [základní třída CodeActivity](../../../docs/framework/windows-workflow-foundation/workflow-activity-authoring-using-the-codeactivity-class.md) a [vytváření asynchronních aktivit](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
 Aktivity, které jsou odvozeny z <xref:System.Activities.NativeActivity> můžete definovat jeho logiku pomocí imperativního kódu a mohou také obsahovat podřízené aktivity, které definují logiku. Mají také úplný přístup k funkcím modulu runtime, jako je například vytváření záložek. Příklady vytvoření <xref:System.Activities.NativeActivity>– na základě aktivity, naleznete v tématu [základní třída NativeActivity](../../../docs/framework/windows-workflow-foundation/nativeactivity-base-class.md), [postupy: vytvoření aktivity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)a [vlastní složené využívající nativní aktivitu](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-using-native-activity.md)vzorku.  
  
 Aktivity, které jsou odvozeny z <xref:System.Activities.Activity> definovat jeho logiku výhradně prostřednictvím podřízené aktivity. Tyto aktivity se obvykle vytvářejí pomocí návrháře postupu provádění, ale můžete také definovat pomocí kódu. V následujícím příkladu `Square` aktivity je definován, která je odvozena z `Activity<int>`. `Square` Aktivita má jeden <xref:System.Activities.InArgument%601> s názvem `Value`a definuje tak, že určíte svou logikou <xref:System.Activities.Statements.Sequence> pomocí aktivity <xref:System.Activities.Activity.Implementation%2A> vlastnost. <xref:System.Activities.Statements.Sequence> Obsahuje aktivity <xref:System.Activities.Statements.WriteLine> aktivity a <xref:System.Activities.Statements.Assign%601> aktivity. Společně tyto tři aktivity implementovat logiku `Square` aktivity.  
  
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
  
 V následujícím příkladu, který se skládá z jedné definice pracovního postupu `Square` aktivity je vyvolán pomocí <xref:System.Activities.WorkflowInvoker>.  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 Když uživatel vyvolá pracovní postup, se zobrazí následující výstup do konzoly:  
  
 **Umocnění na druhou hodnotu: 5**  
**Výsledek: 25**

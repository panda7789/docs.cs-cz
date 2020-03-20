---
title: Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu
ms.date: 03/30/2017
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
ms.openlocfilehash: 7f22880a965274961006f999b1170634377fcf1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183032"
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>Vytváření pracovních postupů, aktivit a výrazů pomocí imperativního kódu
Definice pracovního postupu je strom nakonfigurovaných objektů aktivity. Tento strom aktivit lze definovat mnoha způsoby, včetně ruční úpravy XAML nebo pomocí Návrháře pracovních postupů k výrobě XAML. Použití XAML však není požadavkem. Definice pracovního postupu lze také vytvářet programově. Toto téma obsahuje přehled vytváření definic pracovního postupu, aktivit a výrazů pomocí kódu. Příklady práce s pracovními postupy XAML pomocí kódu naleznete v [tématu Serializace pracovních postupů a aktivit do a z XAML](serializing-workflows-and-activities-to-and-from-xaml.md).  
  
## <a name="creating-workflow-definitions"></a>Vytváření definic pracovního postupu  
 Definici pracovního postupu lze vytvořit vytvořením instance typu aktivity a konfigurací vlastností objektu aktivity. Pro aktivity, které neobsahují podřízené aktivity, to lze provést pomocí několika řádků kódu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
> Příklady v tomto <xref:System.Activities.WorkflowInvoker> tématu slouží ke spuštění ukázkových pracovních postupů. Další informace o vyvolání pracovních postupů, předávání argumentů a různých možností hostování, které jsou k dispozici, naleznete [v tématu Použití WorkflowInvoker a WorkflowApplication](using-workflowinvoker-and-workflowapplication.md).  
  
 V tomto příkladu je vytvořen pracovní <xref:System.Activities.Statements.WriteLine> postup, který se skládá z jedné aktivity. Argument <xref:System.Activities.Statements.WriteLine> aktivity <xref:System.Activities.Statements.WriteLine.Text%2A> je nastaven a pracovní postup je vyvolán. Pokud aktivita obsahuje podřízené aktivity, metoda konstrukce je podobná. Následující příklad používá <xref:System.Activities.Statements.Sequence> aktivitu, <xref:System.Activities.Statements.WriteLine> která obsahuje dvě aktivity.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>Použití inicializátorů objektů  
 Příklady v tomto tématu používají syntaxi inicializace objektu. Syntaxe inicializace objektu může být užitečným způsobem, jak vytvořit definice pracovního postupu v kódu, protože poskytuje hierarchické zobrazení aktivit v pracovním postupu a zobrazuje vztah mezi aktivitami. Při programovém vytváření pracovních postupů není nutné používat syntaxi inicializace objektu. Následující příklad je funkčně ekvivalentní předchozímu příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 Další informace o inicializátorech objektů naleznete v [tématu How to: Initialize Objects without Calling a Constructor (C# Programming Guide)](../../csharp/programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md) a [How to: Declare a Object by Using a Object Initializer](../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md).  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>Práce s proměnnými, literálovými hodnotami a výrazy  
 Při vytváření definice pracovního postupu pomocí kódu si uvědomte, jaký kód se spustí v rámci vytvoření definice pracovního postupu a jaký kód se spustí v rámci provádění instance tohoto pracovního postupu. Následující pracovní postup je například určen ke generování náhodného čísla a jeho zápisu do konzoly.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 Při spuštění tohoto kódu definice pracovního `Random.Next` postupu je provedeno volání a výsledek je uložen v definici pracovního postupu jako literálová hodnota. Mnoho instancí tohoto pracovního postupu lze vyvolat a všechny by zobrazit stejné číslo. Chcete-li mít generování náhodných čísel dojít během provádění pracovního postupu, musí být použit výraz, který je vyhodnocen při každém spuštění pracovního postupu. V následujícím příkladu se výraz jazyka <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>Visual Basic používá s .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Výraz v předchozím příkladu může být <xref:Microsoft.CSharp.Activities.CSharpValue%601> také implementována pomocí a a C# výraz.  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 Výrazy jazyka C# musí být zkompilovány před tím, než je pracovní postup, který je obsahuje, vyvolán. Pokud výrazy Jazyka C# nejsou <xref:System.NotSupportedException> kompilovány, je vyvolána, když je vyvolána ``Expression Activity type 'CSharpValue`1' requires compilation in order to run.  Please ensure that the workflow has been compiled.`` pracovní postup se zprávou podobnou následující: Ve většině scénářů zahrnujících pracovní postupy vytvořené v sadě Visual Studio c# výrazy jsou kompilovány automaticky, ale v některých scénářích, jako je například pracovní postupy kódu, c# výrazy musí být ručně zkompilovány. Příklad kompilace výrazů Jazyka C# naleznete v části [Using C# v](csharp-expressions.md#CodeWorkflows) části pracovní postupy kódu v tématu [C# Expressions.](csharp-expressions.md)  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> představuje výraz v syntaxi jazyka, který lze použít jako hodnotu r ve výrazu a představuje <xref:Microsoft.CSharp.Activities.CSharpValue%601> výraz v syntaxi jazyka C#, který lze použít jako hodnotu r ve výrazu. Tyto výrazy jsou vyhodnocovány při každém spuštění obsahující aktivity. Výsledek výrazu je přiřazen proměnné `n`pracovního postupu a tyto výsledky jsou použity další aktivitou v pracovním postupu. Pro přístup k hodnotě `n` proměnné pracovního <xref:System.Activities.ActivityContext> postupu za běhu je vyžadováno. To lze přistupovat pomocí následujícího výrazu lambda.  
  
> [!NOTE]
> Všimněte si, že oba tyto kódy jsou příklady používají <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> C# jako <xref:Microsoft.CSharp.Activities.CSharpValue%601>programovací jazyk, ale jeden používá a jeden používá . <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>a <xref:Microsoft.CSharp.Activities.CSharpValue%601> lze použít v jazyce Visual Basic a C# projekty. Ve výchozím nastavení výrazy vytvořené v návrháři pracovního postupu odpovídají jazyku hostitelského projektu. Při vytváření pracovních postupů v kódu je požadovaný jazyk na uvážení autora pracovního postupu.  
  
 V těchto příkladech je výsledek výrazu přiřazen `n`proměnné pracovního postupu a tyto výsledky jsou použity další aktivitou v pracovním postupu. Pro přístup k hodnotě `n` proměnné pracovního <xref:System.Activities.ActivityContext> postupu za běhu je vyžadováno. To lze přistupovat pomocí následujícího výrazu lambda.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 Další informace o výrazech lambda naleznete v [tématu Lambda Výrazy (C# Programovací průvodce)](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) nebo [Lambda výrazy (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Lambda výrazy nejsou serializovatelný do formátu XAML. Pokud je proveden pokus o serializaci pracovního postupu s <xref:System.Activities.Expressions.LambdaSerializationException> výrazy lambda, je vyvolána s následující zprávou: "Tento pracovní postup obsahuje výrazy lambda zadané v kódu. Tyto výrazy nelze serializovat v xaml. Chcete-li, aby byl pracovní postup XAML serializovatelný, použijte visualbasicvalue/visualbasicreference nebo expressionservices.convert(lambda). Tím převedete vaše lambda výrazy do výrazu aktivity." Chcete-li tento výraz kompatibilitu <xref:System.Activities.Expressions.ExpressionServices> s <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>XAML, použijte a , jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> by také mohl být použit. Všimněte si, že při použití výrazu jazyka Visual Basic není vyžadován žádný výraz lambda.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 Za běhu jsou výrazy jazyka kompilovány do výrazů LINQ. Oba předchozí příklady jsou serializovatelné na XAML, ale pokud serializované XAML je určena k zobrazení <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> a úpravám v návrháři pracovního postupu, použijte pro vaše výrazy. Serializované pracovní postupy, které lze použít, `ExpressionServices.Convert` lze otevřít v návrháři, ale hodnota výrazu bude prázdná. Další informace o serializaci pracovních postupů do xaml naleznete [v tématu Serializace pracovních postupů a aktivit do a z XAML](serializing-workflows-and-activities-to-and-from-xaml.md).  
  
#### <a name="literal-expressions-and-reference-types"></a>Literálové výrazy a typy odkazů  
 Literál výrazy jsou reprezentovány <xref:System.Activities.Expressions.Literal%601> v pracovních postupech aktivity. Následující <xref:System.Activities.Statements.WriteLine> činnosti jsou funkčně ekvivalentní.  
  
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
  
 Inicializaci literálu s libovolným typem <xref:System.String>odkazu s výjimkou je neplatné . V následujícím příkladu <xref:System.Activities.Statements.Assign> je <xref:System.Activities.Statements.Assign.Value%2A> vlastnost aktivity inicializována `List<string>`literálovým výrazem pomocí .  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 Při ověření pracovního postupu obsahujícího tuto aktivitu je vrácena následující chyba ověření: "Literal podporuje pouze typy hodnot a neměnný typ System.String. Typ System.Collections.Generic.List'1[System.String] nelze použít jako literál." Pokud je vyvolán pracovní <xref:System.Activities.InvalidWorkflowException> postup, je vyvolána, která obsahuje text chyby ověření. Jedná se o chybu ověření, protože vytvoření literálu výrazu s typem odkazu nevytvoří novou instanci typu odkazu pro každou instanci pracovního postupu. Chcete-li tento problém vyřešit, nahraďte literál ový výraz výrazem, který vytvoří a vrátí novou instanci typu odkazu.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 Další informace o výrazech naleznete v [tématu Výrazy](expressions.md).  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>Vyvolání metod u objektů pomocí výrazů a aktivity InvokeMethod  
 Aktivitu <xref:System.Activities.Expressions.InvokeMethod%601> lze použít k vyvolání statických metod a metod instancí tříd v rozhraní .NET Framework. V předchozím příkladu v tomto tématu bylo <xref:System.Random> pomocí třídy generováno náhodné číslo.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Aktivita <xref:System.Activities.Expressions.InvokeMethod%601> mohla být také použita <xref:System.Random.Next%2A> k <xref:System.Random> volání metody třídy.  
  
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
  
 Vzhledem k tomu, <xref:System.Random.Next%2A> že není <xref:System.Random> statickou metodou, je pro vlastnost zadána instance třídy. <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> V tomto příkladu je vytvořena nová instance pomocí výrazu jazyka Visual Basic, ale mohla být také vytvořena dříve a uložena v proměnné pracovního postupu. V tomto příkladu by bylo <xref:System.Activities.Statements.Assign%601> jednodušší použít <xref:System.Activities.Expressions.InvokeMethod%601> aktivitu namísto aktivity. Pokud volání metody nakonec vyvolána <xref:System.Activities.Statements.Assign%601> buď <xref:System.Activities.Expressions.InvokeMethod%601> or aktivity <xref:System.Activities.Expressions.InvokeMethod%601> je dlouho spuštěna, má výhodu, protože má <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> vlastnost. Pokud je tato `true`vlastnost nastavena na , bude metoda vyvolána spuštěna asynchronně s ohledem na pracovní postup. Pokud jsou souběžně jiné aktivity, nebudou blokovány, zatímco metoda je asynchronně provádění. Také pokud metoda, která má být vyvolána <xref:System.Activities.Expressions.InvokeMethod%601> nemá žádnou vrácenou hodnotu, pak je vhodný způsob, jak vyvolat metodu.  
  
## <a name="arguments-and-dynamic-activities"></a>Argumenty a dynamické aktivity  
 Definice pracovního postupu je vytvořena v kódu sestavením aktivit do stromu aktivit a konfigurací všech vlastností a argumentů. Existující argumenty mohou být vázány, ale nové argumenty nelze přidat do aktivit. To zahrnuje argumenty pracovního postupu předané kořenové aktivitě. V imperativním kódu jsou argumenty pracovního postupu určeny jako vlastnosti `x:Class` `x:Member`nového typu CLR a v XAML jsou deklarovány pomocí a . Vzhledem k tomu, že neexistuje žádný nový typ CLR vytvořený při vytvoření definice pracovního postupu jako stromu objektů v paměti, nelze přidat argumenty. Argumenty však lze přidat <xref:System.Activities.DynamicActivity>do . V tomto příkladu <xref:System.Activities.DynamicActivity%601> je vytvořen, který trvá dva celé číslo argumenty, sečte je dohromady a vrátí výsledek. A <xref:System.Activities.DynamicActivityProperty> je vytvořen pro každý argument a výsledek operace <xref:System.Activities.Activity%601.Result%2A> je <xref:System.Activities.DynamicActivity%601>přiřazen k argumentu .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 Další informace o dynamických aktivitách naleznete [v tématu Vytvoření aktivity za běhu](creating-an-activity-at-runtime-with-dynamicactivity.md).  
  
## <a name="compiled-activities"></a>Zkompilované aktivity  
 Dynamické aktivity jsou jedním ze způsobů, jak definovat aktivitu, která obsahuje argumenty pomocí kódu, ale aktivity lze také vytvořit v kódu a zkompilovat do typů. Jednoduché aktivity mohou být <xref:System.Activities.CodeActivity>vytvořeny, které jsou odvozeny <xref:System.Activities.AsyncCodeActivity>z , a asynchronní aktivity, které jsou odvozeny z . Tyto aktivity mohou mít argumenty, vrácené hodnoty a definovat jejich logiku pomocí imperativního kódu. Příklady vytváření těchto typů aktivit naleznete v tématu [CodeActivity Base Class](workflow-activity-authoring-using-the-codeactivity-class.md) a [Creating Asynchronous Activities](creating-asynchronous-activities-in-wf.md).  
  
 Aktivity, <xref:System.Activities.NativeActivity> které jsou odvozeny z můžete definovat jejich logiku pomocí imperativní kód a mohou také obsahovat podřízené aktivity, které definují logiku. Mají také plný přístup k funkcím runtime, jako je vytváření záložek. Příklady vytvoření <xref:System.Activities.NativeActivity>aktivity založené na bázi naleznete v tématu [NativeActivity Base Class](nativeactivity-base-class.md), How [to: Create a Activity](how-to-create-an-activity.md)a Custom Composite using Native [Activity](./samples/custom-composite-using-native-activity.md) sample.  
  
 Aktivity, <xref:System.Activities.Activity> které vyplývají z definovat jejich logiku výhradně pomocí podřízené aktivity. Tyto aktivity jsou obvykle vytvořeny pomocí návrháře pracovního postupu, ale lze také definovat pomocí kódu. V následujícím příkladu `Square` je definována aktivita, která je odvozena od `Activity<int>`. Aktivita `Square` má <xref:System.Activities.InArgument%601> jeden `Value`název a definuje jeho logiku zadáním <xref:System.Activities.Statements.Sequence> aktivity pomocí vlastnosti. <xref:System.Activities.Activity.Implementation%2A> Aktivita <xref:System.Activities.Statements.Sequence> obsahuje <xref:System.Activities.Statements.WriteLine> aktivitu <xref:System.Activities.Statements.Assign%601> a aktivitu. Společně tyto tři činnosti implementovat `Square` logiku aktivity.  
  
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
  
 V následujícím příkladu je pomocí aplikace `Square` vyvolána definice <xref:System.Activities.WorkflowInvoker>pracovního postupu skládající se z jedné aktivity .  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 Při vyvolání pracovního postupu se konzoli zobrazí následující výstup:  
  
 **Srovnat hodnotu: 5**  
**Výsledek: 25**

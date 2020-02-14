---
title: Rozšíření ladění pomocí atributů zobrazení ladicího programu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- debugger, display attributes
- DebuggerTypeProxyAttribute attribute
- debugging [.NET Framework], debugger display attributes
- DebuggerDisplayAttribute attribute
- display attributes for debugger
- DebuggerBrowsableAttribute attribute
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
ms.openlocfilehash: ca118bffb045a0e7e3a5084916a0ff8020ebda90
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216496"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="cf6ed-102">Rozšíření ladění pomocí atributů zobrazení ladicího programu</span><span class="sxs-lookup"><span data-stu-id="cf6ed-102">Enhancing Debugging with the Debugger Display Attributes</span></span>

<span data-ttu-id="cf6ed-103">Atributy zobrazení ladicího programu umožňují vývojáři typu, který určuje a nejlépe porozumět chování za běhu tohoto typu, k určení toho, jaký typ bude vypadat, jako by se zobrazil v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-103">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="cf6ed-104">Kromě toho mohou být atributy zobrazení ladicího programu, které poskytují vlastnost `Target`, na úrovni sestavení aplikovány uživateli bez znalosti zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-104">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="cf6ed-105">Atribut <xref:System.Diagnostics.DebuggerDisplayAttribute> určuje, jak se typ nebo člen zobrazí v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-105">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="cf6ed-106">Atribut <xref:System.Diagnostics.DebuggerBrowsableAttribute> určuje, zda a jak se pole nebo vlastnost zobrazí v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-106">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="cf6ed-107">Atribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> určuje náhradní typ nebo proxy server pro typ a mění způsob, jakým se typ zobrazuje v oknech ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-107">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="cf6ed-108">Pokud zobrazíte proměnnou, která má proxy, nebo náhradní typ, proxy se v okně zobrazí jako původní typ v okně zobrazení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-108">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="cf6ed-109">Okno proměnné ladicího programu zobrazuje pouze veřejné členy typu proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-109">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="cf6ed-110">Soukromé členy nejsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-110">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="cf6ed-111">Použití DebuggerDisplayAttribute –</span><span class="sxs-lookup"><span data-stu-id="cf6ed-111">Using the DebuggerDisplayAttribute</span></span>  

<span data-ttu-id="cf6ed-112">Konstruktor <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> má jeden argument: řetězec, který se má zobrazit ve sloupci value pro instance daného typu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-112">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="cf6ed-113">Tento řetězec může obsahovat složené závorky ({a}).</span><span class="sxs-lookup"><span data-stu-id="cf6ed-113">This string can contain braces ({ and }).</span></span> <span data-ttu-id="cf6ed-114">Text v páru složených závorek je vyhodnocen jako výraz.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-114">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="cf6ed-115">Například následující C# kód způsobí zobrazení "Count = 4", pokud je vybráno znaménko plus (+) pro rozšíření zobrazení ladicího programu pro instanci `MyHashtable`.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-115">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  

```csharp
[DebuggerDisplay("Count = {count}")]
class MyHashtable
{
    public int count = 4;
}
```

<span data-ttu-id="cf6ed-116">Atributy použité na vlastnosti odkazované ve výrazu nejsou zpracovány.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-116">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="cf6ed-117">Pro C# kompilátor je povolen obecný výraz, který má pouze implicitní přístup k tomuto odkazu pro aktuální instanci cílového typu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-117">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="cf6ed-118">Výraz je omezený; není k dispozici žádný přístup k aliasům, místním hodnotám ani ukazatelům.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-118">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="cf6ed-119">V C# kódu můžete použít obecný výraz mezi složenými závorkami, které mají implicitní přístup k ukazateli `this` pro aktuální instanci cílového typu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-119">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>

<span data-ttu-id="cf6ed-120">Například pokud je C# objekt přepsaný `ToString()`, ladicí program bude volat přepsání a namísto standardního `{<typeName>}.` zobrazit jeho výsledek, takže pokud jste přepsali `ToString()`, nemusíte používat <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-120">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="cf6ed-121">Použijete-li obojí, atribut <xref:System.Diagnostics.DebuggerDisplayAttribute> má přednost před přepsáním `ToString()`.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-121">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>

## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="cf6ed-122">Použití DebuggerBrowsableAttribute</span><span class="sxs-lookup"><span data-stu-id="cf6ed-122">Using the DebuggerBrowsableAttribute</span></span>
 <span data-ttu-id="cf6ed-123">Použijte <xref:System.Diagnostics.DebuggerBrowsableAttribute> pro pole nebo vlastnost k určení, jak se má pole nebo vlastnost zobrazovat v okně ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-123">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="cf6ed-124">Konstruktor pro tento atribut přijímá jednu z <xref:System.Diagnostics.DebuggerBrowsableState> hodnot výčtu, která určuje jeden z následujících stavů:</span><span class="sxs-lookup"><span data-stu-id="cf6ed-124">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>

- <span data-ttu-id="cf6ed-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> označuje, že člen není zobrazen v okně data.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="cf6ed-126">Například použití této hodnoty pro <xref:System.Diagnostics.DebuggerBrowsableAttribute> v poli odebere pole z hierarchie; pole se nezobrazí, když rozbalíte nadřazený typ kliknutím na znaménko plus (+) pro instanci typu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-126">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>

- <span data-ttu-id="cf6ed-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> označuje, že se člen zobrazuje, ale ve výchozím nastavení není rozbalený.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="cf6ed-128">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-128">This is the default behavior.</span></span>

- <span data-ttu-id="cf6ed-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> označuje, že samotný člen není zobrazen, ale jeho prvky jsou zobrazeny, pokud se jedná o pole nebo kolekci.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>

> [!NOTE]
> <span data-ttu-id="cf6ed-130"><xref:System.Diagnostics.DebuggerBrowsableAttribute> není podporován Visual Basic v .NET Framework verzi 2,0.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-130">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>

<span data-ttu-id="cf6ed-131">Následující příklad kódu ukazuje použití <xref:System.Diagnostics.DebuggerBrowsableAttribute>, aby se zabránilo tomu, aby se vlastnost po ní zobrazovala v okně ladění pro třídu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-131">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>

```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]
public static string y = "Test String";
```

## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="cf6ed-132">Použití používání DebuggerTypeProxy</span><span class="sxs-lookup"><span data-stu-id="cf6ed-132">Using the DebuggerTypeProxy</span></span>
 <span data-ttu-id="cf6ed-133">Atribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> použijte v případě, že potřebujete významně a zásadním způsobem změnit zobrazení ladění typu, ale neměňte samotný typ.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-133">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="cf6ed-134">Atribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> slouží k určení zobrazovaného proxy serveru pro určitý typ, který vývojářům umožňuje přizpůsobit zobrazení pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-134">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="cf6ed-135">Tento atribut, jako je <xref:System.Diagnostics.DebuggerDisplayAttribute>, lze použít na úrovni sestavení. v takovém případě vlastnost <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> určuje typ, pro který bude použit proxy server.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-135">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="cf6ed-136">Doporučené použití je, že tento atribut určuje soukromý vnořený typ, který se vyskytuje v rámci typu, na který je atribut použit.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-136">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="cf6ed-137">Vyhodnocovací filtr výrazů, který podporuje posluchače typu pro tento atribut při zobrazení typu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-137">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="cf6ed-138">Pokud je atribut nalezen, vyhodnocení výrazu nahradí typ proxy zobrazení pro typ, na který je atribut použit.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-138">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>

 <span data-ttu-id="cf6ed-139">Pokud je k dispozici <xref:System.Diagnostics.DebuggerTypeProxyAttribute>, okno proměnné ladicího programu zobrazí pouze veřejné členy typu proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-139">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="cf6ed-140">Soukromé členy nejsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-140">Private members are not displayed.</span></span> <span data-ttu-id="cf6ed-141">Chování okna data se v zobrazeních s rozšířenými atributy nemění.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-141">The behavior of the data window is not changed by attribute-enhanced views.</span></span>

 <span data-ttu-id="cf6ed-142">Aby nedocházelo k zbytečnému vlivu na výkon, atributy zobrazení proxy nejsou zpracovány, dokud není objekt rozbalen, a to buď po kliknutí na znaménko plus (+) vedle typu v okně dat, nebo prostřednictvím aplikace atributu <xref:System.Diagnostics.DebuggerBrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-142">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="cf6ed-143">Proto se doporučuje, aby se pro typ zobrazení nepoužívaly žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-143">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="cf6ed-144">Atributy mohou a by měly být aplikovány v těle typu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-144">Attributes can and should be applied within the body of the display type.</span></span>

 <span data-ttu-id="cf6ed-145">Následující příklad kódu ukazuje použití <xref:System.Diagnostics.DebuggerTypeProxyAttribute> k určení typu, který se má použít jako proxy zobrazení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-145">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>

```csharp
[DebuggerTypeProxy(typeof(HashtableDebugView))]
class MyHashtable : Hashtable
{
    private const string TestString =
        "This should not appear in the debug window.";

    internal class HashtableDebugView
    {
        private Hashtable hashtable;
        public const string TestStringProxy =
            "This should appear in the debug window.";

        // The constructor for the type proxy class must have a
        // constructor that takes the target type as a parameter.
        public HashtableDebugView(Hashtable hashtable)
        {
            this.hashtable = hashtable;
        }
    }
}
```

## <a name="example"></a><span data-ttu-id="cf6ed-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="cf6ed-146">Example</span></span>

### <a name="description"></a><span data-ttu-id="cf6ed-147">Popis</span><span class="sxs-lookup"><span data-stu-id="cf6ed-147">Description</span></span>

<span data-ttu-id="cf6ed-148">Následující příklad kódu lze zobrazit v aplikaci Visual Studio pro zobrazení výsledků použití atributů <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>a <xref:System.Diagnostics.DebuggerTypeProxyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cf6ed-148">The following code example can be viewed in Visual Studio to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>

### <a name="code"></a><span data-ttu-id="cf6ed-149">Kód</span><span class="sxs-lookup"><span data-stu-id="cf6ed-149">Code</span></span>

[!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
[!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
[!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="cf6ed-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf6ed-150">See also</span></span>

- <xref:System.Diagnostics.DebuggerDisplayAttribute>
- <xref:System.Diagnostics.DebuggerBrowsableAttribute>
- <xref:System.Diagnostics.DebuggerTypeProxyAttribute>

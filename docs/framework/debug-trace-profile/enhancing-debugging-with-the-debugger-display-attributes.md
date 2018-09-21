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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 880504e874d9797cf05290058b6dbf3a3daf2579
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46473113"
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="0ac72-102">Rozšíření ladění pomocí atributů zobrazení ladicího programu</span><span class="sxs-lookup"><span data-stu-id="0ac72-102">Enhancing Debugging with the Debugger Display Attributes</span></span>
<span data-ttu-id="0ac72-103">Povolit vývojář atributů zobrazení ladicího programu typu, který určuje a nejlépe rozumí chování za běhu tohoto typu, také určit, co typu bude vypadat jako, který se zobrazí v ladicí program.</span><span class="sxs-lookup"><span data-stu-id="0ac72-103">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="0ac72-104">Kromě toho ladicí program zobrazit atributy, které poskytují `Target` vlastnost jde použít na úrovni sestavení uživatelé bez vědomí zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-104">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="0ac72-105"><xref:System.Diagnostics.DebuggerDisplayAttribute> Atribut určuje, jak je zobrazeno typ nebo člen v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-105">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="0ac72-106"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Atribut určuje, zda a jak pole nebo vlastnost se zobrazí v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-106">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="0ac72-107"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atribut určuje náhradní typ. nebo proxy server, pro typ a změní způsob, jak se zobrazí typ v oknech ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-107">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="0ac72-108">Při zobrazení proměnná, která má proxy server nebo náhradní typ. proxy zastupuje původní typ, v okně zobrazení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-108">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window.</span></span> <span data-ttu-id="0ac72-109">V okně proměnné ladicího programu se zobrazí pouze veřejné členy typu proxy.</span><span class="sxs-lookup"><span data-stu-id="0ac72-109">The debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="0ac72-110">Soukromé členy nejsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="0ac72-110">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="0ac72-111">Použití debuggerdisplayattribute –</span><span class="sxs-lookup"><span data-stu-id="0ac72-111">Using the DebuggerDisplayAttribute</span></span>  
 <span data-ttu-id="0ac72-112"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Konstruktor obsahuje jediný argument: řetězec, který se zobrazí ve sloupci Hodnota pro instance daného typu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-112">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="0ac72-113">Tento řetězec může obsahovat složených závorek ({a}).</span><span class="sxs-lookup"><span data-stu-id="0ac72-113">This string can contain braces ({ and }).</span></span> <span data-ttu-id="0ac72-114">Text v rámci dvojici závorek je vyhodnocen jako výraz.</span><span class="sxs-lookup"><span data-stu-id="0ac72-114">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="0ac72-115">Například následující kód jazyka C# způsobí, že se "Count = 4" který se má zobrazit, pokud je vybrána na symbol plus (+) rozbalte zobrazení ladicího programu pro instanci `MyHashtable`.</span><span class="sxs-lookup"><span data-stu-id="0ac72-115">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  
  
```csharp
[DebuggerDisplay("Count = {count}")]  
class MyHashtable  
{  
    public int count = 4;  
}  
```
  
 <span data-ttu-id="0ac72-116">Atributy použité na vlastnosti odkazuje ve výrazu nebudou zpracovány.</span><span class="sxs-lookup"><span data-stu-id="0ac72-116">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="0ac72-117">Pro kompilátor jazyka C# je povolen obecné výraz, který má pouze implicitní přístup k tomuto odkazu pro aktuální instanci cílového typu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-117">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="0ac72-118">Výraz je omezená; není k dispozici přístup pro aliasy, místní hodnoty nebo ukazatele.</span><span class="sxs-lookup"><span data-stu-id="0ac72-118">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="0ac72-119">V kódu jazyka C#, můžete použít obecné výraz mezi závorkami, ke kterým implicitní přístup `this` ukazatele pro aktuální instanci pouze cílového typu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-119">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>  
  
 <span data-ttu-id="0ac72-120">Například, pokud objekt jazyka C# má překryté `ToString()`, ladicí program bude volat přepsání a zobrazit její výsledek místo standardní `{<typeName>}.` proto pokud mají přepsat `ToString()`, není potřeba použít <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0ac72-120">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="0ac72-121">Pokud používáte obě, <xref:System.Diagnostics.DebuggerDisplayAttribute> atribut má přednost před `ToString()` přepsat.</span><span class="sxs-lookup"><span data-stu-id="0ac72-121">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>  
  
## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="0ac72-122">Použití debuggerbrowsableattribute –</span><span class="sxs-lookup"><span data-stu-id="0ac72-122">Using the DebuggerBrowsableAttribute</span></span>  
 <span data-ttu-id="0ac72-123">Použít <xref:System.Diagnostics.DebuggerBrowsableAttribute> pole nebo vlastnosti a určit, jak pole nebo vlastnost se zobrazí v okně ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-123">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="0ac72-124">Konstruktor pro tento atribut má jednu z <xref:System.Diagnostics.DebuggerBrowsableState> hodnot výčtu, které určuje jeden z následujících stavů:</span><span class="sxs-lookup"><span data-stu-id="0ac72-124">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>  
  
-   <span data-ttu-id="0ac72-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> Označuje, že člen není zobrazen v okně data.</span><span class="sxs-lookup"><span data-stu-id="0ac72-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="0ac72-126">Například použití pro tuto hodnotu <xref:System.Diagnostics.DebuggerBrowsableAttribute> na pole odstraní pole z hierarchie; pole se nezobrazí, pokud rozšiřujete nadřazeného typu. Kliknutím na symbol plus (+) pro instanci typu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-126">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>  
  
-   <span data-ttu-id="0ac72-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> Označuje, že člen je zobrazen ale nebyla rozšířená. ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="0ac72-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="0ac72-128">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="0ac72-128">This is the default behavior.</span></span>  
  
-   <span data-ttu-id="0ac72-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> Označuje, že samotný člen není zobrazen, ale jeho základní objektů se zobrazí, pokud je pole nebo kolekce.</span><span class="sxs-lookup"><span data-stu-id="0ac72-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ac72-130"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Nepodporuje Visual Basic v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="0ac72-130">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="0ac72-131">Následující příklad kódu ukazuje použití <xref:System.Diagnostics.DebuggerBrowsableAttribute> zabránit vlastnost následující povolí, v okně ladění pro třídu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-131">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>  
  
```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]  
public static string y = "Test String";  
```  
  
## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="0ac72-132">Použití DebuggerTypeProxy</span><span class="sxs-lookup"><span data-stu-id="0ac72-132">Using the DebuggerTypeProxy</span></span>  
 <span data-ttu-id="0ac72-133">Použití <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atribut, když budete chtít v podstatě a výrazně změnit zobrazení ladění typu, ale nikoli změnit samotného typu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-133">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="0ac72-134"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atribut se používá k určení zobrazení proxy pro typ, povolení pro vývojáře pro přizpůsobení zobrazení typu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-134">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="0ac72-135">Tento atribut, jako je třeba <xref:System.Diagnostics.DebuggerDisplayAttribute>, lze použít na úrovni sestavení, v takovém případě <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> vlastnost určuje typ, pro který se použije proxy server.</span><span class="sxs-lookup"><span data-stu-id="0ac72-135">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="0ac72-136">Doporučuje, aby tento atribut určuje privátní vnořený typ, který se nachází v rámci typu, ke kterému se atribut používá.</span><span class="sxs-lookup"><span data-stu-id="0ac72-136">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="0ac72-137">Vyhodnocovače výrazů, podporuje typ kontroly prohlížeče pro tento atribut při zobrazení typu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-137">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="0ac72-138">Pokud se najde atribut vyhodnocovací filtr výrazů nahradí zobrazení proxy server, zadejte pro typ atributu se použije na.</span><span class="sxs-lookup"><span data-stu-id="0ac72-138">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>  
  
 <span data-ttu-id="0ac72-139">Když <xref:System.Diagnostics.DebuggerTypeProxyAttribute> je k dispozici, v okně proměnné ladicího programu se zobrazí pouze veřejné členy typ proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="0ac72-139">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="0ac72-140">Soukromé členy nejsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="0ac72-140">Private members are not displayed.</span></span> <span data-ttu-id="0ac72-141">Chování okna data se nemění podle atribut rozšířeného zobrazení.</span><span class="sxs-lookup"><span data-stu-id="0ac72-141">The behavior of the data window is not changed by attribute-enhanced views.</span></span>  
  
 <span data-ttu-id="0ac72-142">Aby se zabránilo snížení výkonu zbytečné, atributy proxy zobrazení nezpracovávají, dokud nebude objekt rozbalen, až uživatel kliknutím na symbol plus (+) vedle typ v okně data nebo prostřednictvím použití <xref:System.Diagnostics.DebuggerBrowsableAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="0ac72-142">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="0ac72-143">Doporučujeme proto, že žádné atributy použít pro typ zobrazení.</span><span class="sxs-lookup"><span data-stu-id="0ac72-143">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="0ac72-144">Atributy lze a bude použito v těle typ zobrazení.</span><span class="sxs-lookup"><span data-stu-id="0ac72-144">Attributes can and should be applied within the body of the display type.</span></span>  
  
 <span data-ttu-id="0ac72-145">Následující příklad kódu ukazuje použití <xref:System.Diagnostics.DebuggerTypeProxyAttribute> zadat typ má být použit jako proxy server zobrazení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="0ac72-145">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="0ac72-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ac72-146">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="0ac72-147">Popis</span><span class="sxs-lookup"><span data-stu-id="0ac72-147">Description</span></span>  
 <span data-ttu-id="0ac72-148">Následující příklad kódu lze zobrazit v [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] zobrazíte výsledky použití <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, a <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atributy.</span><span class="sxs-lookup"><span data-stu-id="0ac72-148">The following code example can be viewed in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>  
  
### <a name="code"></a><span data-ttu-id="0ac72-149">Kód</span><span class="sxs-lookup"><span data-stu-id="0ac72-149">Code</span></span>  
 [!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
 [!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
 [!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0ac72-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ac72-150">See Also</span></span>  
 <xref:System.Diagnostics.DebuggerDisplayAttribute>  
 <xref:System.Diagnostics.DebuggerBrowsableAttribute>  
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>

---
title: "Rozšíření ladění pomocí atributů zobrazení ladicího programu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac5097326ae76a8790569c13fd8b1285b0cfeec0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="enhancing-debugging-with-the-debugger-display-attributes"></a><span data-ttu-id="73dc6-102">Rozšíření ladění pomocí atributů zobrazení ladicího programu</span><span class="sxs-lookup"><span data-stu-id="73dc6-102">Enhancing Debugging with the Debugger Display Attributes</span></span>
<span data-ttu-id="73dc6-103">Atributů zobrazení ladicího programu povolit vývojář typu, který určuje a nejlépe rozumí modul runtime chování tohoto typu, také určit, co daný typ bude vypadat, který se zobrazí v ladicí program.</span><span class="sxs-lookup"><span data-stu-id="73dc6-103">Debugger display attributes allow the developer of the type, who specifies and best understands the runtime behavior of that type, to also specify what that type will look like when it is displayed in a debugger.</span></span> <span data-ttu-id="73dc6-104">Kromě toho ladicí program atributy, které poskytují zobrazení `Target` vlastnost lze použít na úrovni sestavení uživatelé bez vědomí zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="73dc6-104">In addition, debugger display attributes that provide a `Target` property can be applied at the assembly level by users without knowledge of the source code.</span></span> <span data-ttu-id="73dc6-105"><xref:System.Diagnostics.DebuggerDisplayAttribute> Atribut ovládací prvky zobrazení typ nebo člen v proměnnými ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="73dc6-105">The <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute controls how a type or member is displayed in the debugger variable windows.</span></span> <span data-ttu-id="73dc6-106"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Atribut určuje, zda a jak pole nebo vlastnost je zobrazena v proměnnými ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="73dc6-106">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute determines if and how a field or property is displayed in the debugger variable windows.</span></span> <span data-ttu-id="73dc6-107"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atribut určuje typ substitute nebo proxy server, pro typ a mění způsob přidělování typ se zobrazí v ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="73dc6-107">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute specifies a substitute type, or a proxy, for a type and changes the way the type is displayed in debugger windows.</span></span> <span data-ttu-id="73dc6-108">Při zobrazení proměnné, která má proxy server, nebo nahraďte typ proxy serveru znamená původní typ v okně zobrazení ladicího programu**.**</span><span class="sxs-lookup"><span data-stu-id="73dc6-108">When you view a variable that has a proxy, or substitute type, the proxy stands in for the original type in the debugger display window**.**</span></span> <span data-ttu-id="73dc6-109">Zadejte pouze veřejné členy proxy proměnné windowdisplays ladicí program.</span><span class="sxs-lookup"><span data-stu-id="73dc6-109">The debugger variable windowdisplays only the public members of the proxy type.</span></span> <span data-ttu-id="73dc6-110">Soukromé členy nejsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="73dc6-110">Private members are not displayed.</span></span>  
  
## <a name="using-the-debuggerdisplayattribute"></a><span data-ttu-id="73dc6-111">Pomocí DebuggerDisplayAttribute</span><span class="sxs-lookup"><span data-stu-id="73dc6-111">Using the DebuggerDisplayAttribute</span></span>  
 <span data-ttu-id="73dc6-112"><xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> Konstruktor má jeden argument: řetězec, který se zobrazí ve sloupci Hodnota pro instance typu.</span><span class="sxs-lookup"><span data-stu-id="73dc6-112">The <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> constructor has a single argument: a string to be displayed in the value column for instances of the type.</span></span> <span data-ttu-id="73dc6-113">Tento řetězec může obsahovat složené závorky ({a}).</span><span class="sxs-lookup"><span data-stu-id="73dc6-113">This string can contain braces ({ and }).</span></span> <span data-ttu-id="73dc6-114">Text v páru složených závorek je vyhodnoceno jako výraz.</span><span class="sxs-lookup"><span data-stu-id="73dc6-114">The text within a pair of braces is evaluated as an expression.</span></span> <span data-ttu-id="73dc6-115">Například následující kód C# způsobí "Count = 4" na zobrazí, když je vybrán znaménko plus (+) rozbalte zobrazení ladicího programu pro instanci `MyHashtable`.</span><span class="sxs-lookup"><span data-stu-id="73dc6-115">For example, the following C# code causes "Count = 4" to be displayed when the plus sign (+) is selected to expand the debugger display for an instance of `MyHashtable`.</span></span>  
  
```csharp
[DebuggerDisplay("Count = {count}")]  
class MyHashtable  
{  
    public int count = 4;  
}  
```
  
 <span data-ttu-id="73dc6-116">Atributy použité na vlastnosti odkazován ve výrazu nejsou předmětem zpracování.</span><span class="sxs-lookup"><span data-stu-id="73dc6-116">Attributes applied to properties referenced in the expression are not processed.</span></span> <span data-ttu-id="73dc6-117">Pro kompilátor jazyka C# je povolen obecné výraz, který má jenom implicitní přístup na tento odkaz pro aktuální instancí třídy na typ cíle.</span><span class="sxs-lookup"><span data-stu-id="73dc6-117">For the C# compiler, a general expression is allowed that has only implicit access to this reference for the current instance of the target type.</span></span> <span data-ttu-id="73dc6-118">Výraz je omezená; není k dispozici přístup k aliasy, místní hodnoty nebo ukazatele.</span><span class="sxs-lookup"><span data-stu-id="73dc6-118">The expression is limited; there is no access to aliases, locals, or pointers.</span></span> <span data-ttu-id="73dc6-119">V kódu jazyka C#, můžete použít výraz obecné mezi složené závorky, které má implicitní přístup k `this` ukazatele pro aktuální instancí třídy na typ cíle.</span><span class="sxs-lookup"><span data-stu-id="73dc6-119">In C# code, you can use a general expression between the braces that has implicit access to the `this` pointer for the current instance of the target type only.</span></span>  
  
 <span data-ttu-id="73dc6-120">Například, pokud má objekt C# překryté `ToString()`, ladicí program zavolá přepsání a zobrazit její výsledek místo standardní `{<typeName>}.` zacílí, pokud mají přepsat `ToString()`, není potřeba použít <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="73dc6-120">For example, if a C# object has an overridden `ToString()`, the debugger will call the override and show its result instead of the standard `{<typeName>}.` Thus, if you have overridden `ToString()`, you do not need to use <xref:System.Diagnostics.DebuggerDisplayAttribute>.</span></span> <span data-ttu-id="73dc6-121">Pokud používáte obě, <xref:System.Diagnostics.DebuggerDisplayAttribute> atribut má přednost před `ToString()` přepsat.</span><span class="sxs-lookup"><span data-stu-id="73dc6-121">If you use both, the <xref:System.Diagnostics.DebuggerDisplayAttribute> attribute takes precedence over the `ToString()` override.</span></span>  
  
## <a name="using-the-debuggerbrowsableattribute"></a><span data-ttu-id="73dc6-122">Pomocí debuggerbrowsableattribute –</span><span class="sxs-lookup"><span data-stu-id="73dc6-122">Using the DebuggerBrowsableAttribute</span></span>  
 <span data-ttu-id="73dc6-123">Použít <xref:System.Diagnostics.DebuggerBrowsableAttribute> pole nebo vlastnost k určení, jak pole nebo vlastnost se zobrazí v okně ladicí program.</span><span class="sxs-lookup"><span data-stu-id="73dc6-123">Apply the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to a field or property to specify how the field or property is to be displayed in the debugger window.</span></span> <span data-ttu-id="73dc6-124">V konstruktoru pro tento atribut má jednu z <xref:System.Diagnostics.DebuggerBrowsableState> hodnoty výčtu, které určuje jednu z následujících stavů:</span><span class="sxs-lookup"><span data-stu-id="73dc6-124">The constructor for this attribute takes one of the <xref:System.Diagnostics.DebuggerBrowsableState> enumeration values, which specifies one of the following states:</span></span>  
  
-   <span data-ttu-id="73dc6-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never>Označuje, že člen není zobrazen v okně data.</span><span class="sxs-lookup"><span data-stu-id="73dc6-125"><xref:System.Diagnostics.DebuggerBrowsableState.Never> indicates that the member is not displayed in the data window.</span></span>  <span data-ttu-id="73dc6-126">Například pomocí této hodnoty pro <xref:System.Diagnostics.DebuggerBrowsableAttribute> na pole odebere pole z hierarchie; pole se nezobrazí, pokud rozbalíte kliknutím na symbol plus (+) pro instanci typu nadřazených typů.</span><span class="sxs-lookup"><span data-stu-id="73dc6-126">For example, using this value for the <xref:System.Diagnostics.DebuggerBrowsableAttribute> on a field removes the field from the hierarchy; the field is not displayed when you expand the enclosing type by clicking the plus sign (+) for the type instance.</span></span>  
  
-   <span data-ttu-id="73dc6-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed>Označuje, že je člen zobrazí ale není rozšířit ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="73dc6-127"><xref:System.Diagnostics.DebuggerBrowsableState.Collapsed> indicates that the member is displayed but not expanded by default.</span></span>  <span data-ttu-id="73dc6-128">Toto je výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="73dc6-128">This is the default behavior.</span></span>  
  
-   <span data-ttu-id="73dc6-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden>Určuje, že člena samotného není vidět, ale pokud je pole nebo kolekce, zobrazí se jeho základní objekty.</span><span class="sxs-lookup"><span data-stu-id="73dc6-129"><xref:System.Diagnostics.DebuggerBrowsableState.RootHidden> indicates that the member itself is not shown, but its constituent objects are displayed if it is an array or collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73dc6-130"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Nepodporuje Visual Basic v rozhraní .NET Framework verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="73dc6-130">The <xref:System.Diagnostics.DebuggerBrowsableAttribute> is not supported by Visual Basic in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="73dc6-131">Následující příklad kódu ukazuje použití <xref:System.Diagnostics.DebuggerBrowsableAttribute> aby vlastnost následující zobrazování v okně ladění pro třídu.</span><span class="sxs-lookup"><span data-stu-id="73dc6-131">The following code example shows the use of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> to prevent the property following it from appearing in the debug window for the class.</span></span>  
  
```csharp
[DebuggerBrowsable(DebuggerBrowsableState.Never)]  
public static string y = "Test String";  
```  
  
## <a name="using-the-debuggertypeproxy"></a><span data-ttu-id="73dc6-132">Pomocí DebuggerTypeProxy</span><span class="sxs-lookup"><span data-stu-id="73dc6-132">Using the DebuggerTypeProxy</span></span>  
 <span data-ttu-id="73dc6-133">Použití <xref:System.Diagnostics.DebuggerTypeProxyAttribute> Pokud budete potřebovat výrazně a zásadně změnit zobrazení ladění typu, ale neumožňuje změnit vlastní typ atributu.</span><span class="sxs-lookup"><span data-stu-id="73dc6-133">Use the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute when you need to significantly and fundamentally change the debugging view of a type, but not change the type itself.</span></span> <span data-ttu-id="73dc6-134"><xref:System.Diagnostics.DebuggerTypeProxyAttribute> Atribut slouží k určení zobrazení proxy pro typ, což vývojáře k přizpůsobit zobrazení pro typ.</span><span class="sxs-lookup"><span data-stu-id="73dc6-134">The <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attribute is used to specify a display proxy for a type, allowing a developer to tailor the view for the type.</span></span>  <span data-ttu-id="73dc6-135">Tento atribut, jako je třeba <xref:System.Diagnostics.DebuggerDisplayAttribute>, lze použít na úrovni sestavení, v takovém případě <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> vlastnost určuje typ, pro který se použije k proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="73dc6-135">This attribute, like the <xref:System.Diagnostics.DebuggerDisplayAttribute>, can be used at the assembly level, in which case the <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> property specifies the type for which the proxy will be used.</span></span> <span data-ttu-id="73dc6-136">Doporučené využití je, že tento atribut určuje privátní vnořené typy, který se vyskytuje v typu, na který se použije atribut.</span><span class="sxs-lookup"><span data-stu-id="73dc6-136">The recommended usage is that this attribute specifies a private nested type that occurs within the type to which the attribute is applied.</span></span>  <span data-ttu-id="73dc6-137">Vyhodnocení výrazu, podporuje typ prohlížeče kontroluje pro tento atribut, když se zobrazí typu.</span><span class="sxs-lookup"><span data-stu-id="73dc6-137">An expression evaluator that supports type viewers checks for this attribute when a type is displayed.</span></span> <span data-ttu-id="73dc6-138">Pokud je nalezen atribut, nahradí vyhodnocovací filtr výrazů zobrazení typ proxy pro typ atributu se použije na.</span><span class="sxs-lookup"><span data-stu-id="73dc6-138">If the attribute is found, the expression evaluator substitutes the display proxy type for the type the attribute is applied to.</span></span>  
  
 <span data-ttu-id="73dc6-139">Když <xref:System.Diagnostics.DebuggerTypeProxyAttribute> je k dispozici, v okně proměnné ladicí program se zobrazí pouze veřejné členy typ proxy.</span><span class="sxs-lookup"><span data-stu-id="73dc6-139">When the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> is present, the debugger variable window displays only the public members of the proxy type.</span></span> <span data-ttu-id="73dc6-140">Soukromé členy nejsou zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="73dc6-140">Private members are not displayed.</span></span> <span data-ttu-id="73dc6-141">Chování okna dat není změnit atribut rozšířeného zobrazení.</span><span class="sxs-lookup"><span data-stu-id="73dc6-141">The behavior of the data window is not changed by attribute-enhanced views.</span></span>  
  
 <span data-ttu-id="73dc6-142">Aby nedošlo k penalizaci zbytečně výkon, nebudou zpracovány atributy zobrazení proxy, dokud objekt je rozšířena prostřednictvím uživatel kliknutím na symbol plus (+) vedle typu v okně data nebo prostřednictvím použití <xref:System.Diagnostics.DebuggerBrowsableAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="73dc6-142">To avoid unnecessary performance penalties, attributes of the display proxy are not processed until the object is expanded, either through the user clicking the plus sign (+) next to the type in a data window, or through the application of the <xref:System.Diagnostics.DebuggerBrowsableAttribute> attribute.</span></span> <span data-ttu-id="73dc6-143">Proto se doporučuje, aby se žádné atributy použijí na typ zobrazení.</span><span class="sxs-lookup"><span data-stu-id="73dc6-143">Therefore, it is recommended that no attributes be applied to the display type.</span></span> <span data-ttu-id="73dc6-144">Atributy může a měla by se použít v textu typu zobrazení.</span><span class="sxs-lookup"><span data-stu-id="73dc6-144">Attributes can and should be applied within the body of the display type.</span></span>  
  
 <span data-ttu-id="73dc6-145">Následující příklad kódu ukazuje použití <xref:System.Diagnostics.DebuggerTypeProxyAttribute> k určení typu, který se má použít jako proxy server zobrazení ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="73dc6-145">The following code example shows the use of the <xref:System.Diagnostics.DebuggerTypeProxyAttribute> to specify a type to be used as a debugger display proxy.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="73dc6-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="73dc6-146">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="73dc6-147">Popis</span><span class="sxs-lookup"><span data-stu-id="73dc6-147">Description</span></span>  
 <span data-ttu-id="73dc6-148">Následující příklad kódu lze zobrazit v [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] a zobrazte si výsledky použití <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, a <xref:System.Diagnostics.DebuggerTypeProxyAttribute> atributy.</span><span class="sxs-lookup"><span data-stu-id="73dc6-148">The following code example can be viewed in [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] to see the results of applying the <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute>, and <xref:System.Diagnostics.DebuggerTypeProxyAttribute> attributes.</span></span>  
  
### <a name="code"></a><span data-ttu-id="73dc6-149">Kód</span><span class="sxs-lookup"><span data-stu-id="73dc6-149">Code</span></span>  
 [!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
 [!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
 [!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="73dc6-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="73dc6-150">See Also</span></span>  
 <xref:System.Diagnostics.DebuggerDisplayAttribute>  
 <xref:System.Diagnostics.DebuggerBrowsableAttribute>  
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>

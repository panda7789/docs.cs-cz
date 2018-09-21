---
title: 'Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET Framework (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 9a17aaec20b03325abadfcc168f7ac4653f300df
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46471129"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="641f5-102">Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET Framework (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="641f5-102">How to: Publish Events that Conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="641f5-103">Následující postup ukazuje, jak přidat události, které dodržovat standardní [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vzor, který má třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="641f5-103">The following procedure demonstrates how to add events that follow the standard [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pattern to your classes and structs.</span></span> <span data-ttu-id="641f5-104">Všechny události v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] knihovny tříd jsou založeny na <xref:System.EventHandler> delegovat, která je definovaná následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="641f5-104">All events in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  <span data-ttu-id="641f5-105">[!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] Představuje obecné verzi tohoto delegáta <xref:System.EventHandler%601>.</span><span class="sxs-lookup"><span data-stu-id="641f5-105">The [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="641f5-106">Následující příklady ukazují, jak použít obě verze.</span><span class="sxs-lookup"><span data-stu-id="641f5-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="641f5-107">I když události ve třídách, které definujete, může být založené na libovolný platný delegát i delegáty, které vrací hodnotu, obecně doporučujeme založit událostí na [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vzor s použitím <xref:System.EventHandler>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="641f5-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="641f5-108">Chcete-li publikovat události založena na vzoru obslužná rutina události</span><span class="sxs-lookup"><span data-stu-id="641f5-108">To publish events based on the EventHandler pattern</span></span>  
  
1.  <span data-ttu-id="641f5-109">(Tento krok přeskočit a přejít na krok 3a, pokud nemáte k odesílání vlastních dat s vaší události.) Deklarování třídy pro vaše vlastní data v oboru, který je viditelný na vydavatele a odběratele třídy.</span><span class="sxs-lookup"><span data-stu-id="641f5-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="641f5-110">Pak přidejte požadované členy k uchování dat vlastních událostí.</span><span class="sxs-lookup"><span data-stu-id="641f5-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="641f5-111">V tomto příkladu je vrácena jednoduchým řetězcem.</span><span class="sxs-lookup"><span data-stu-id="641f5-111">In this example, a simple string is returned.</span></span>  
  
    ```csharp  
    public class CustomEventArgs : EventArgs  
    {  
        public CustomEventArgs(string s)  
        {  
            msg = s;  
        }  
        private string msg;  
        public string Message  
        {  
            get { return msg; }  
        }   
    }  
    ```  
  
2.  <span data-ttu-id="641f5-112">(Tento krok přeskočte, pokud používáte obecné verzi <xref:System.EventHandler%601> .) Deklarujte delegáta ve své třídě pro publikování.</span><span class="sxs-lookup"><span data-stu-id="641f5-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="641f5-113">Přiřaďte jí název, který končí *EventHandler*.</span><span class="sxs-lookup"><span data-stu-id="641f5-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="641f5-114">Druhý parametr určuje vašeho vlastního typu EventArgs.</span><span class="sxs-lookup"><span data-stu-id="641f5-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  <span data-ttu-id="641f5-115">Deklarujte událost ve své třídě pro publikování pomocí jedné z následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="641f5-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1.  <span data-ttu-id="641f5-116">Pokud žádné vlastní třídu EventArgs, bude váš typ události delegáta EventHandler Obecné.</span><span class="sxs-lookup"><span data-stu-id="641f5-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="641f5-117">Nemusíte deklarovat delegáta, protože je již deklarován <xref:System> obor názvů, který je součástí při vytváření projektu C#.</span><span class="sxs-lookup"><span data-stu-id="641f5-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="641f5-118">Přidejte následující kód do třídy vydavatele.</span><span class="sxs-lookup"><span data-stu-id="641f5-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  <span data-ttu-id="641f5-119">Pokud používáte verzi neobecnou <xref:System.EventHandler> a máte vlastní třídy odvozené od <xref:System.EventArgs>deklarovat událost uvnitř publikování třídy a použít jako typ delegáta z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="641f5-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3.  <span data-ttu-id="641f5-120">Pokud používáte obecné verzi, není nutné vlastního delegáta.</span><span class="sxs-lookup"><span data-stu-id="641f5-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="641f5-121">Místo toho ve své třídě publikování zadáte jako typ události `EventHandler<CustomEventArgs>`, kde nahradíte název vlastní třídy mezi ostrých závorek.</span><span class="sxs-lookup"><span data-stu-id="641f5-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="641f5-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="641f5-122">Example</span></span>  
 <span data-ttu-id="641f5-123">Následující příklad ukazuje v předchozích krocích pomocí vlastní třídy EventArgs a <xref:System.EventHandler%601> jako typ události.</span><span class="sxs-lookup"><span data-stu-id="641f5-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="641f5-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="641f5-124">See Also</span></span>

- <xref:System.Delegate>  
- [<span data-ttu-id="641f5-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="641f5-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="641f5-126">Události</span><span class="sxs-lookup"><span data-stu-id="641f5-126">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="641f5-127">Delegáti</span><span class="sxs-lookup"><span data-stu-id="641f5-127">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)

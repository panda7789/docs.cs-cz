---
title: Jak publikovat události, které jsou v souladu s pokyny rozhraní .NET Framework – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 90c079b9f7dbf2a1d963b7eee4447145d7a10432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167530"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="e163f-102">Jak publikovat události, které odpovídají pokynům rozhraní .NET Framework (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e163f-102">How to publish events that conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="e163f-103">Následující postup ukazuje, jak přidat události, které následují standardní .NET Framework vzor vaše třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="e163f-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="e163f-104">Všechny události v knihovně tříd rozhraní <xref:System.EventHandler> .NET Framework jsou založeny na delegátovi, který je definován takto:</span><span class="sxs-lookup"><span data-stu-id="e163f-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> <span data-ttu-id="e163f-105">Rozhraní .NET Framework 2.0 zavádí obecnou verzi <xref:System.EventHandler%601>tohoto delegáta .</span><span class="sxs-lookup"><span data-stu-id="e163f-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="e163f-106">Následující příklady ukazují, jak používat obě verze.</span><span class="sxs-lookup"><span data-stu-id="e163f-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="e163f-107">Přestože události ve třídách, které definujete, mohou být založeny na libovolném platném typu delegáta, dokonce <xref:System.EventHandler>i delegáti, kteří vracejí hodnotu, obecně se doporučuje založit události na vzoru rozhraní .NET Framework pomocí , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e163f-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="e163f-108">Publikování událostí na základě vzoru EventHandler</span><span class="sxs-lookup"><span data-stu-id="e163f-108">To publish events based on the EventHandler pattern</span></span>  
  
1. <span data-ttu-id="e163f-109">(Tento krok přeskočte a přejděte ke kroku 3a, pokud s událostí nemusíte odesílat vlastní data.) Deklarujte třídu pro vlastní data v oboru, který je viditelný pro třídy vydavatele i odběratele.</span><span class="sxs-lookup"><span data-stu-id="e163f-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="e163f-110">Pak přidejte požadované členy pro uložení vlastních dat událostí.</span><span class="sxs-lookup"><span data-stu-id="e163f-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="e163f-111">V tomto příkladu je vrácen jednoduchý řetězec.</span><span class="sxs-lookup"><span data-stu-id="e163f-111">In this example, a simple string is returned.</span></span>  
  
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
  
2. <span data-ttu-id="e163f-112">(Tento krok přeskočte, pokud <xref:System.EventHandler%601> používáte obecnou verzi aplikace .) Deklarujte delegáta ve třídě publikování.</span><span class="sxs-lookup"><span data-stu-id="e163f-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="e163f-113">Pojmenujte jej, který končí *na EventHandler*.</span><span class="sxs-lookup"><span data-stu-id="e163f-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="e163f-114">Druhý parametr určuje váš vlastní Typ EventArgs.</span><span class="sxs-lookup"><span data-stu-id="e163f-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. <span data-ttu-id="e163f-115">Deklarujte událost ve vaší třídě publikování pomocí jednoho z následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="e163f-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1. <span data-ttu-id="e163f-116">Pokud nemáte vlastní třídu EventArgs, bude vaším typem události neobecný delegát EventHandler.</span><span class="sxs-lookup"><span data-stu-id="e163f-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="e163f-117">Není nutné deklarovat delegáta, protože <xref:System> je již deklarována v oboru názvů, který je součástí při vytváření projektu Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="e163f-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="e163f-118">Přidejte do třídy vydavatele následující kód.</span><span class="sxs-lookup"><span data-stu-id="e163f-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. <span data-ttu-id="e163f-119">Pokud používáte neobecnou verzi <xref:System.EventHandler> aplikace a máte vlastní třídu odvozenou z <xref:System.EventArgs>aplikace , deklarujte událost uvnitř třídy publikování a jako typ použijte delegáta z kroku 2.</span><span class="sxs-lookup"><span data-stu-id="e163f-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. <span data-ttu-id="e163f-120">Pokud používáte obecnou verzi, nepotřebujete vlastního delegáta.</span><span class="sxs-lookup"><span data-stu-id="e163f-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="e163f-121">Místo toho ve třídě publikování zadáte typ `EventHandler<CustomEventArgs>`události jako , který napočne název vlastní třídy mezi úhlovými závorkami.</span><span class="sxs-lookup"><span data-stu-id="e163f-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="e163f-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="e163f-122">Example</span></span>  
 <span data-ttu-id="e163f-123">Následující příklad ukazuje předchozí kroky pomocí vlastní Třídy <xref:System.EventHandler%601> EventArgs a jako typ události.</span><span class="sxs-lookup"><span data-stu-id="e163f-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e163f-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="e163f-124">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="e163f-125">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e163f-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e163f-126">Akce</span><span class="sxs-lookup"><span data-stu-id="e163f-126">Events</span></span>](./index.md)
- [<span data-ttu-id="e163f-127">Delegáty</span><span class="sxs-lookup"><span data-stu-id="e163f-127">Delegates</span></span>](../delegates/index.md)

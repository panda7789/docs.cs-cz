---
title: 'Postupy: Publikování událostí vyhovujících pravidlům .NET Framework – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 93924638fabe9a46af39006130d4f07de2ad0541
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590476"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="aa73e-102">Postupy: Publikovat události, které jsou v souladu sC# pokyny pro .NET Framework (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="aa73e-102">How to: Publish Events that Conform to .NET Framework Guidelines (C# Programming Guide)</span></span>
<span data-ttu-id="aa73e-103">Následující postup ukazuje, jak přidat události, které následují standardní .NET Framework vzor, pro vaše třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="aa73e-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="aa73e-104">Všechny události v knihovně tříd .NET Framework jsou založeny na <xref:System.EventHandler> delegátu, který je definován následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="aa73e-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  <span data-ttu-id="aa73e-105">.NET Framework 2,0 zavádí obecnou verzi tohoto delegáta <xref:System.EventHandler%601>.</span><span class="sxs-lookup"><span data-stu-id="aa73e-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="aa73e-106">Následující příklady ukazují, jak používat obě verze.</span><span class="sxs-lookup"><span data-stu-id="aa73e-106">The following examples show how to use both versions.</span></span>  
  
 <span data-ttu-id="aa73e-107">I když události v třídách, které definujete, mohou být založeny na jakémkoli platném typu delegáta, dokonce i delegáti, kteří vrací hodnotu, obecně se doporučuje, abyste zavedli <xref:System.EventHandler>své události na vzor .NET Framework pomocí, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="aa73e-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="aa73e-108">Publikování událostí na základě vzoru EventHandler</span><span class="sxs-lookup"><span data-stu-id="aa73e-108">To publish events based on the EventHandler pattern</span></span>  
  
1. <span data-ttu-id="aa73e-109">(Tento krok přeskočte a přejděte na Krok 3a, pokud nemusíte odesílat vlastní data s událostí.) Deklarujte třídu pro vlastní data v oboru, který je viditelný pro třídy Vydavatel a odběratel.</span><span class="sxs-lookup"><span data-stu-id="aa73e-109">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="aa73e-110">Pak přidejte požadované členy, které budou uchovávat vaše vlastní data události.</span><span class="sxs-lookup"><span data-stu-id="aa73e-110">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="aa73e-111">V tomto příkladu je vrácen jednoduchý řetězec.</span><span class="sxs-lookup"><span data-stu-id="aa73e-111">In this example, a simple string is returned.</span></span>  
  
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
  
2. <span data-ttu-id="aa73e-112">(Tento krok přeskočte, pokud používáte obecnou verzi <xref:System.EventHandler%601> .) Deklarujete delegáta ve třídě publikování.</span><span class="sxs-lookup"><span data-stu-id="aa73e-112">(Skip this step if you are using the generic version of <xref:System.EventHandler%601> .) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="aa73e-113">Dejte mu název, který končí na *události EventHandler*.</span><span class="sxs-lookup"><span data-stu-id="aa73e-113">Give it a name that ends with *EventHandler*.</span></span> <span data-ttu-id="aa73e-114">Druhý parametr určuje vlastní typ EventArgs.</span><span class="sxs-lookup"><span data-stu-id="aa73e-114">The second parameter specifies your custom EventArgs type.</span></span>  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. <span data-ttu-id="aa73e-115">Deklarujte událost ve třídě pro publikování pomocí jednoho z následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="aa73e-115">Declare the event in your publishing class by using one of the following steps.</span></span>  
  
    1. <span data-ttu-id="aa73e-116">Pokud nemáte žádnou vlastní třídu EventArgs, váš typ události bude neobecný Delegát EventHandler.</span><span class="sxs-lookup"><span data-stu-id="aa73e-116">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="aa73e-117">Není nutné deklarovat delegáta, protože je již deklarována v <xref:System> oboru názvů, který je zahrnut při vytváření C# projektu.</span><span class="sxs-lookup"><span data-stu-id="aa73e-117">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="aa73e-118">Přidejte následující kód do třídy Vydavatel.</span><span class="sxs-lookup"><span data-stu-id="aa73e-118">Add the following code to your publisher class.</span></span>  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. <span data-ttu-id="aa73e-119">Pokud používáte neobecnou verzi <xref:System.EventHandler> nástroje a máte vlastní třídu odvozenou z <xref:System.EventArgs>, deklarujte událost uvnitř třídy publikování a použijte svého delegáta z kroku 2 jako typ.</span><span class="sxs-lookup"><span data-stu-id="aa73e-119">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. <span data-ttu-id="aa73e-120">Pokud používáte obecnou verzi, nepotřebujete vlastního delegáta.</span><span class="sxs-lookup"><span data-stu-id="aa73e-120">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="aa73e-121">Místo toho ve své třídě publikování určíte typ události jako `EventHandler<CustomEventArgs>`a nahrazením názvu vlastní třídy mezi lomenými závorkami.</span><span class="sxs-lookup"><span data-stu-id="aa73e-121">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a><span data-ttu-id="aa73e-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="aa73e-122">Example</span></span>  
 <span data-ttu-id="aa73e-123">Následující příklad ukazuje předchozí kroky pomocí vlastní třídy EventArgs a <xref:System.EventHandler%601> jako typ události.</span><span class="sxs-lookup"><span data-stu-id="aa73e-123">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="aa73e-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa73e-124">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="aa73e-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="aa73e-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="aa73e-126">Události</span><span class="sxs-lookup"><span data-stu-id="aa73e-126">Events</span></span>](./index.md)
- [<span data-ttu-id="aa73e-127">Delegáti</span><span class="sxs-lookup"><span data-stu-id="aa73e-127">Delegates</span></span>](../delegates/index.md)

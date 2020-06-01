---
title: Publikovat události, které odpovídají pravidlům rozhraní .NET – Průvodce programováním v C#
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: df2f643f867b93b74d04d8fbd673df545c28938e
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240743"
---
# <a name="how-to-publish-events-that-conform-to-net-guidelines-c-programming-guide"></a><span data-ttu-id="ae2fe-102">Jak publikovat události, které jsou v souladu s pokyny rozhraní .NET (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ae2fe-102">How to publish events that conform to .NET Guidelines (C# Programming Guide)</span></span>

<span data-ttu-id="ae2fe-103">Následující postup ukazuje, jak přidat události, které následují standardní vzor .NET, pro vaše třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-103">The following procedure demonstrates how to add events that follow the standard .NET pattern to your classes and structs.</span></span> <span data-ttu-id="ae2fe-104">Všechny události v knihovně tříd .NET Framework jsou založeny na <xref:System.EventHandler> delegátu, který je definován následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ae2fe-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> <span data-ttu-id="ae2fe-105">.NET Framework 2,0 zavádí obecnou verzi tohoto delegáta <xref:System.EventHandler%601> .</span><span class="sxs-lookup"><span data-stu-id="ae2fe-105">.NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="ae2fe-106">Následující příklady ukazují, jak používat obě verze.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-106">The following examples show how to use both versions.</span></span>

<span data-ttu-id="ae2fe-107">I když události v třídách, které definujete, mohou být založeny na jakémkoli platném typu delegáta, dokonce i delegáti, kteří vrací hodnotu, obecně se doporučuje, abyste zavedli své události na vzor .NET pomocí <xref:System.EventHandler> , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>

<span data-ttu-id="ae2fe-108">Název `EventHandler` může vést k nejasnostem, protože ve skutečnosti událost nezpracovává.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-108">The name `EventHandler` can lead to a bit of confusion as it doesn't actually handle the event.</span></span> <span data-ttu-id="ae2fe-109"><xref:System.EventHandler>A obecné <xref:System.EventHandler%601> jsou typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-109">The <xref:System.EventHandler>, and generic <xref:System.EventHandler%601> are delegate types.</span></span> <span data-ttu-id="ae2fe-110">Metoda nebo výraz lambda, jehož signatura odpovídá definici delegáta, je *obslužná rutina události* a bude vyvolána při vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-110">A method or lambda expression whose signature matches the delegate definition is the *event handler* and will be invoked when the event is raised.</span></span>

## <a name="publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="ae2fe-111">Publikování událostí na základě vzoru EventHandler</span><span class="sxs-lookup"><span data-stu-id="ae2fe-111">Publish events based on the EventHandler pattern</span></span>

1. <span data-ttu-id="ae2fe-112">(Tento krok přeskočte a přejděte na Krok 3a, pokud nemusíte odesílat vlastní data s událostí.) Deklarujte třídu pro vlastní data v oboru, který je viditelný pro třídy Vydavatel a odběratel.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-112">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="ae2fe-113">Pak přidejte požadované členy, které budou uchovávat vaše vlastní data události.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-113">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="ae2fe-114">V tomto příkladu je vrácen jednoduchý řetězec.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-114">In this example, a simple string is returned.</span></span>

    ```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }

        public string Message { get; set; }
    }
    ```

2. <span data-ttu-id="ae2fe-115">(Tento krok přeskočte, pokud používáte obecnou verzi <xref:System.EventHandler%601> .) Deklarujete delegáta ve třídě publikování.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-115">(Skip this step if you are using the generic version of <xref:System.EventHandler%601>.) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="ae2fe-116">Dejte mu název, který končí na `EventHandler` .</span><span class="sxs-lookup"><span data-stu-id="ae2fe-116">Give it a name that ends with `EventHandler`.</span></span> <span data-ttu-id="ae2fe-117">Druhý parametr určuje váš vlastní `EventArgs` typ.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-117">The second parameter specifies your custom `EventArgs` type.</span></span>

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. <span data-ttu-id="ae2fe-118">Deklarujte událost ve třídě pro publikování pomocí jednoho z následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-118">Declare the event in your publishing class by using one of the following steps.</span></span>

    1. <span data-ttu-id="ae2fe-119">Pokud nemáte žádnou vlastní třídu EventArgs, váš typ události bude neobecný Delegát EventHandler.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-119">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="ae2fe-120">Nemusíte deklarovat delegáta, protože je již deklarována v <xref:System> oboru názvů, který je zahrnutý při vytváření projektu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-120">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="ae2fe-121">Přidejte následující kód do třídy Vydavatel.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-121">Add the following code to your publisher class.</span></span>

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. <span data-ttu-id="ae2fe-122">Pokud používáte neobecnou verzi nástroje <xref:System.EventHandler> a máte vlastní třídu odvozenou z <xref:System.EventArgs> , deklarujte událost uvnitř třídy publikování a použijte svého delegáta z kroku 2 jako typ.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-122">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. <span data-ttu-id="ae2fe-123">Pokud používáte obecnou verzi, nepotřebujete vlastního delegáta.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-123">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="ae2fe-124">Místo toho ve své třídě publikování určíte typ události jako `EventHandler<CustomEventArgs>` a nahrazením názvu vlastní třídy mezi lomenými závorkami.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-124">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a><span data-ttu-id="ae2fe-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae2fe-125">Example</span></span>

<span data-ttu-id="ae2fe-126">Následující příklad ukazuje předchozí kroky pomocí vlastní třídy EventArgs a <xref:System.EventHandler%601> jako typ události.</span><span class="sxs-lookup"><span data-stu-id="ae2fe-126">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a><span data-ttu-id="ae2fe-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae2fe-127">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="ae2fe-128">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ae2fe-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ae2fe-129">Události</span><span class="sxs-lookup"><span data-stu-id="ae2fe-129">Events</span></span>](index.md)
- [<span data-ttu-id="ae2fe-130">Delegáti</span><span class="sxs-lookup"><span data-stu-id="ae2fe-130">Delegates</span></span>](../delegates/index.md)

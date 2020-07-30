---
title: Publikovat události, které odpovídají pravidlům rozhraní .NET – Průvodce programováním v C#
description: Naučte se publikovat události, které jsou v souladu s pokyny pro rozhraní .NET. Všechny události v knihovně tříd .NET Framework jsou založeny na delegátu EventHandler.
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 1b802e236026911b55bafcb3f48d487c43bba174
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302110"
---
# <a name="how-to-publish-events-that-conform-to-net-guidelines-c-programming-guide"></a><span data-ttu-id="319e5-104">Jak publikovat události, které jsou v souladu s pokyny rozhraní .NET (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="319e5-104">How to publish events that conform to .NET Guidelines (C# Programming Guide)</span></span>

<span data-ttu-id="319e5-105">Následující postup ukazuje, jak přidat události, které následují standardní vzor .NET, pro vaše třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="319e5-105">The following procedure demonstrates how to add events that follow the standard .NET pattern to your classes and structs.</span></span> <span data-ttu-id="319e5-106">Všechny události v knihovně tříd .NET Framework jsou založeny na <xref:System.EventHandler> delegátu, který je definován následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="319e5-106">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> <span data-ttu-id="319e5-107">.NET Framework 2,0 zavádí obecnou verzi tohoto delegáta <xref:System.EventHandler%601> .</span><span class="sxs-lookup"><span data-stu-id="319e5-107">.NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="319e5-108">Následující příklady ukazují, jak používat obě verze.</span><span class="sxs-lookup"><span data-stu-id="319e5-108">The following examples show how to use both versions.</span></span>

<span data-ttu-id="319e5-109">I když události v třídách, které definujete, mohou být založeny na jakémkoli platném typu delegáta, dokonce i delegáti, kteří vrací hodnotu, obecně se doporučuje, abyste zavedli své události na vzor .NET pomocí <xref:System.EventHandler> , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="319e5-109">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>

<span data-ttu-id="319e5-110">Název `EventHandler` může vést k nejasnostem, protože ve skutečnosti událost nezpracovává.</span><span class="sxs-lookup"><span data-stu-id="319e5-110">The name `EventHandler` can lead to a bit of confusion as it doesn't actually handle the event.</span></span> <span data-ttu-id="319e5-111"><xref:System.EventHandler>A obecné <xref:System.EventHandler%601> jsou typy delegátů.</span><span class="sxs-lookup"><span data-stu-id="319e5-111">The <xref:System.EventHandler>, and generic <xref:System.EventHandler%601> are delegate types.</span></span> <span data-ttu-id="319e5-112">Metoda nebo výraz lambda, jehož signatura odpovídá definici delegáta, je *obslužná rutina události* a bude vyvolána při vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="319e5-112">A method or lambda expression whose signature matches the delegate definition is the *event handler* and will be invoked when the event is raised.</span></span>

## <a name="publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="319e5-113">Publikování událostí na základě vzoru EventHandler</span><span class="sxs-lookup"><span data-stu-id="319e5-113">Publish events based on the EventHandler pattern</span></span>

1. <span data-ttu-id="319e5-114">(Tento krok přeskočte a přejděte na Krok 3a, pokud nemusíte odesílat vlastní data s událostí.) Deklarujte třídu pro vlastní data v oboru, který je viditelný pro třídy Vydavatel a odběratel.</span><span class="sxs-lookup"><span data-stu-id="319e5-114">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="319e5-115">Pak přidejte požadované členy, které budou uchovávat vaše vlastní data události.</span><span class="sxs-lookup"><span data-stu-id="319e5-115">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="319e5-116">V tomto příkladu je vrácen jednoduchý řetězec.</span><span class="sxs-lookup"><span data-stu-id="319e5-116">In this example, a simple string is returned.</span></span>

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

2. <span data-ttu-id="319e5-117">(Tento krok přeskočte, pokud používáte obecnou verzi <xref:System.EventHandler%601> .) Deklarujete delegáta ve třídě publikování.</span><span class="sxs-lookup"><span data-stu-id="319e5-117">(Skip this step if you are using the generic version of <xref:System.EventHandler%601>.) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="319e5-118">Dejte mu název, který končí na `EventHandler` .</span><span class="sxs-lookup"><span data-stu-id="319e5-118">Give it a name that ends with `EventHandler`.</span></span> <span data-ttu-id="319e5-119">Druhý parametr určuje váš vlastní `EventArgs` typ.</span><span class="sxs-lookup"><span data-stu-id="319e5-119">The second parameter specifies your custom `EventArgs` type.</span></span>

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. <span data-ttu-id="319e5-120">Deklarujte událost ve třídě pro publikování pomocí jednoho z následujících kroků.</span><span class="sxs-lookup"><span data-stu-id="319e5-120">Declare the event in your publishing class by using one of the following steps.</span></span>

    1. <span data-ttu-id="319e5-121">Pokud nemáte žádnou vlastní třídu EventArgs, váš typ události bude neobecný Delegát EventHandler.</span><span class="sxs-lookup"><span data-stu-id="319e5-121">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="319e5-122">Nemusíte deklarovat delegáta, protože je již deklarována v <xref:System> oboru názvů, který je zahrnutý při vytváření projektu jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="319e5-122">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="319e5-123">Přidejte následující kód do třídy Vydavatel.</span><span class="sxs-lookup"><span data-stu-id="319e5-123">Add the following code to your publisher class.</span></span>

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. <span data-ttu-id="319e5-124">Pokud používáte neobecnou verzi nástroje <xref:System.EventHandler> a máte vlastní třídu odvozenou z <xref:System.EventArgs> , deklarujte událost uvnitř třídy publikování a použijte svého delegáta z kroku 2 jako typ.</span><span class="sxs-lookup"><span data-stu-id="319e5-124">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. <span data-ttu-id="319e5-125">Pokud používáte obecnou verzi, nepotřebujete vlastního delegáta.</span><span class="sxs-lookup"><span data-stu-id="319e5-125">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="319e5-126">Místo toho ve své třídě publikování určíte typ události jako `EventHandler<CustomEventArgs>` a nahrazením názvu vlastní třídy mezi lomenými závorkami.</span><span class="sxs-lookup"><span data-stu-id="319e5-126">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a><span data-ttu-id="319e5-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="319e5-127">Example</span></span>

<span data-ttu-id="319e5-128">Následující příklad ukazuje předchozí kroky pomocí vlastní třídy EventArgs a <xref:System.EventHandler%601> jako typ události.</span><span class="sxs-lookup"><span data-stu-id="319e5-128">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a><span data-ttu-id="319e5-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="319e5-129">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="319e5-130">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="319e5-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="319e5-131">Události</span><span class="sxs-lookup"><span data-stu-id="319e5-131">Events</span></span>](index.md)
- [<span data-ttu-id="319e5-132">Delegáti</span><span class="sxs-lookup"><span data-stu-id="319e5-132">Delegates</span></span>](../delegates/index.md)

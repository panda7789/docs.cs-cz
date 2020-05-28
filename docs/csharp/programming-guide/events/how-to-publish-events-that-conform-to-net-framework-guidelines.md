---
title: Postup publikování událostí, které odpovídají pravidlům .NET Framework – Průvodce programováním v C#
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 137e52b80703491a4528a3eddc7fa12f9dce6f52
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144796"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Jak publikovat události, které jsou v souladu s pokyny pro .NET Framework (Průvodce programováním v C#)

Následující postup ukazuje, jak přidat události, které následují standardní .NET Framework vzor, pro vaše třídy a struktury. Všechny události v knihovně tříd .NET Framework jsou založeny na <xref:System.EventHandler> delegátu, který je definován následujícím způsobem:

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> .NET Framework 2,0 zavádí obecnou verzi tohoto delegáta <xref:System.EventHandler%601> . Následující příklady ukazují, jak používat obě verze.

I když události v třídách, které definujete, mohou být založeny na jakémkoli platném typu delegáta, dokonce i delegáti, kteří vrací hodnotu, obecně se doporučuje, abyste zavedli své události na vzor .NET Framework pomocí <xref:System.EventHandler> , jak je znázorněno v následujícím příkladu.

Název `EventHandler` může vést k nejasnostem, protože ve skutečnosti událost nezpracovává. <xref:System.EventHandler>A obecné <xref:System.EventHandler%601> jsou typy delegátů. Metoda nebo výraz lambda, jehož signatura odpovídá definici delegáta, je *obslužná rutina události* a bude vyvolána při vyvolání události.

### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Publikování událostí na základě vzoru EventHandler

1. (Tento krok přeskočte a přejděte na Krok 3a, pokud nemusíte odesílat vlastní data s událostí.) Deklarujte třídu pro vlastní data v oboru, který je viditelný pro třídy Vydavatel a odběratel. Pak přidejte požadované členy, které budou uchovávat vaše vlastní data události. V tomto příkladu je vrácen jednoduchý řetězec.

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

2. (Tento krok přeskočte, pokud používáte obecnou verzi <xref:System.EventHandler%601> .) Deklarujete delegáta ve třídě publikování. Dejte mu název, který končí na `EventHandler` . Druhý parametr určuje váš vlastní `EventArgs` typ.

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. Deklarujte událost ve třídě pro publikování pomocí jednoho z následujících kroků.

    1. Pokud nemáte žádnou vlastní třídu EventArgs, váš typ události bude neobecný Delegát EventHandler. Nemusíte deklarovat delegáta, protože je již deklarována v <xref:System> oboru názvů, který je zahrnutý při vytváření projektu jazyka C#. Přidejte následující kód do třídy Vydavatel.

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. Pokud používáte neobecnou verzi nástroje <xref:System.EventHandler> a máte vlastní třídu odvozenou z <xref:System.EventArgs> , deklarujte událost uvnitř třídy publikování a použijte svého delegáta z kroku 2 jako typ.

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. Pokud používáte obecnou verzi, nepotřebujete vlastního delegáta. Místo toho ve své třídě publikování určíte typ události jako `EventHandler<CustomEventArgs>` a nahrazením názvu vlastní třídy mezi lomenými závorkami.

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a>Příklad

Následující příklad ukazuje předchozí kroky pomocí vlastní třídy EventArgs a <xref:System.EventHandler%601> jako typ události.

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a>Viz také

- <xref:System.Delegate>
- [Průvodce programováním v C#](../index.md)
- [Události](index.md)
- [Delegáti](../delegates/index.md)

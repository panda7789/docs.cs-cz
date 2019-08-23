---
title: 'Postupy: Publikování událostí vyhovujících pravidlům .NET Framework – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 8cf0f57caad41da0a29b935029731260154a2dc7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924022"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Postupy: Publikovat události, které jsou v souladu sC# pokyny pro .NET Framework (Průvodce programováním)
Následující postup ukazuje, jak přidat události, které následují standardní .NET Framework vzor, pro vaše třídy a struktury. Všechny události v knihovně tříd .NET Framework jsou založeny na <xref:System.EventHandler> delegátu, který je definován následujícím způsobem:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> .NET Framework 2,0 zavádí obecnou verzi tohoto delegáta <xref:System.EventHandler%601>. Následující příklady ukazují, jak používat obě verze.  
  
 I když události v třídách, které definujete, mohou být založeny na jakémkoli platném typu delegáta, dokonce i delegáti, kteří vrací hodnotu, obecně se doporučuje, abyste zavedli <xref:System.EventHandler>své události na vzor .NET Framework pomocí, jak je znázorněno v následujícím příkladu.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Publikování událostí na základě vzoru EventHandler  
  
1. (Tento krok přeskočte a přejděte na Krok 3a, pokud nemusíte odesílat vlastní data s událostí.) Deklarujte třídu pro vlastní data v oboru, který je viditelný pro třídy Vydavatel a odběratel. Pak přidejte požadované členy, které budou uchovávat vaše vlastní data události. V tomto příkladu je vrácen jednoduchý řetězec.  
  
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
  
2. (Tento krok přeskočte, pokud používáte obecnou verzi <xref:System.EventHandler%601> .) Deklarujete delegáta ve třídě publikování. Dejte mu název, který končí na *události EventHandler*. Druhý parametr určuje vlastní typ EventArgs.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. Deklarujte událost ve třídě pro publikování pomocí jednoho z následujících kroků.  
  
    1. Pokud nemáte žádnou vlastní třídu EventArgs, váš typ události bude neobecný Delegát EventHandler. Není nutné deklarovat delegáta, protože je již deklarována v <xref:System> oboru názvů, který je zahrnut při vytváření C# projektu. Přidejte následující kód do třídy Vydavatel.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. Pokud používáte neobecnou verzi <xref:System.EventHandler> nástroje a máte vlastní třídu odvozenou z <xref:System.EventArgs>, deklarujte událost uvnitř třídy publikování a použijte svého delegáta z kroku 2 jako typ.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. Pokud používáte obecnou verzi, nepotřebujete vlastního delegáta. Místo toho ve své třídě publikování určíte typ události jako `EventHandler<CustomEventArgs>`a nahrazením názvu vlastní třídy mezi lomenými závorkami.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje předchozí kroky pomocí vlastní třídy EventArgs a <xref:System.EventHandler%601> jako typ události.  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Delegate>
- [Průvodce programováním v jazyce C#](../index.md)
- [Události](./index.md)
- [Delegáti](../delegates/index.md)

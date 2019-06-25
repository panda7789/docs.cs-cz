---
title: 'Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET Framework – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 8af6d7d91efef81569e6f783352ec89d260cdd13
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347604"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET (C# Průvodce programováním v)
Následující postup ukazuje, jak přidat události, které mají tvar standardní rozhraní .NET Framework do vaší třídy a struktury. Všechny události v knihovně tříd rozhraní .NET Framework jsou založeny na <xref:System.EventHandler> delegovat, která je definovaná následujícím způsobem:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  Rozhraní .NET Framework 2.0 představuje obecné verzi tohoto delegáta <xref:System.EventHandler%601>. Následující příklady ukazují, jak použít obě verze.  
  
 I když události ve třídách, které definujete, může být založené na libovolný platný delegát i delegáty, které vrací hodnotu, se obecně doporučuje základní události v rozhraní .NET Framework model s použitím <xref:System.EventHandler>, jak je znázorněno v následujícím příkladu.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Chcete-li publikovat události založena na vzoru obslužná rutina události  
  
1. (Tento krok přeskočit a přejít na krok 3a, pokud nemáte k odesílání vlastních dat s vaší události.) Deklarování třídy pro vaše vlastní data v oboru, který je viditelný na vydavatele a odběratele třídy. Pak přidejte požadované členy k uchování dat vlastních událostí. V tomto příkladu je vrácena jednoduchým řetězcem.  
  
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
  
2. (Tento krok přeskočte, pokud používáte obecné verzi <xref:System.EventHandler%601> .) Deklarujte delegáta ve své třídě pro publikování. Přiřaďte jí název, který končí *EventHandler*. Druhý parametr určuje vašeho vlastního typu EventArgs.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. Deklarujte událost ve své třídě pro publikování pomocí jedné z následujících kroků.  
  
    1. Pokud žádné vlastní třídu EventArgs, bude váš typ události delegáta EventHandler Obecné. Nemusíte deklarovat delegáta, protože je již deklarován <xref:System> obor názvů, který je součástí při vytváření projektu C#. Přidejte následující kód do třídy vydavatele.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. Pokud používáte verzi neobecnou <xref:System.EventHandler> a máte vlastní třídy odvozené od <xref:System.EventArgs>deklarovat událost uvnitř publikování třídy a použít jako typ delegáta z kroku 2.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. Pokud používáte obecné verzi, není nutné vlastního delegáta. Místo toho ve své třídě publikování zadáte jako typ události `EventHandler<CustomEventArgs>`, kde nahradíte název vlastní třídy mezi ostrých závorek.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje v předchozích krocích pomocí vlastní třídy EventArgs a <xref:System.EventHandler%601> jako typ události.  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Delegate>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Události](../../../csharp/programming-guide/events/index.md)
- [Delegáti](../../../csharp/programming-guide/delegates/index.md)

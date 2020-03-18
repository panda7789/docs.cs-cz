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
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Jak publikovat události, které odpovídají pokynům rozhraní .NET Framework (Průvodce programováním jazyka C#)
Následující postup ukazuje, jak přidat události, které následují standardní .NET Framework vzor vaše třídy a struktury. Všechny události v knihovně tříd rozhraní <xref:System.EventHandler> .NET Framework jsou založeny na delegátovi, který je definován takto:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
> Rozhraní .NET Framework 2.0 zavádí obecnou verzi <xref:System.EventHandler%601>tohoto delegáta . Následující příklady ukazují, jak používat obě verze.  
  
 Přestože události ve třídách, které definujete, mohou být založeny na libovolném platném typu delegáta, dokonce <xref:System.EventHandler>i delegáti, kteří vracejí hodnotu, obecně se doporučuje založit události na vzoru rozhraní .NET Framework pomocí , jak je znázorněno v následujícím příkladu.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Publikování událostí na základě vzoru EventHandler  
  
1. (Tento krok přeskočte a přejděte ke kroku 3a, pokud s událostí nemusíte odesílat vlastní data.) Deklarujte třídu pro vlastní data v oboru, který je viditelný pro třídy vydavatele i odběratele. Pak přidejte požadované členy pro uložení vlastních dat událostí. V tomto příkladu je vrácen jednoduchý řetězec.  
  
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
  
2. (Tento krok přeskočte, pokud <xref:System.EventHandler%601> používáte obecnou verzi aplikace .) Deklarujte delegáta ve třídě publikování. Pojmenujte jej, který končí *na EventHandler*. Druhý parametr určuje váš vlastní Typ EventArgs.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3. Deklarujte událost ve vaší třídě publikování pomocí jednoho z následujících kroků.  
  
    1. Pokud nemáte vlastní třídu EventArgs, bude vaším typem události neobecný delegát EventHandler. Není nutné deklarovat delegáta, protože <xref:System> je již deklarována v oboru názvů, který je součástí při vytváření projektu Jazyka C#. Přidejte do třídy vydavatele následující kód.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2. Pokud používáte neobecnou verzi <xref:System.EventHandler> aplikace a máte vlastní třídu odvozenou z <xref:System.EventArgs>aplikace , deklarujte událost uvnitř třídy publikování a jako typ použijte delegáta z kroku 2.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3. Pokud používáte obecnou verzi, nepotřebujete vlastního delegáta. Místo toho ve třídě publikování zadáte typ `EventHandler<CustomEventArgs>`události jako , který napočne název vlastní třídy mezi úhlovými závorkami.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje předchozí kroky pomocí vlastní Třídy <xref:System.EventHandler%601> EventArgs a jako typ události.  
  
 [!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Delegate>
- [Programovací příručka jazyka C#](../index.md)
- [Akce](./index.md)
- [Delegáty](../delegates/index.md)

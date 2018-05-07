---
title: 'Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET Framework (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 830f86be43f1499bd87ff02690061b08f8f7f86d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a>Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET Framework (Průvodce programováním v C#)
Následující postup ukazuje, jak přidat události, které následují standardní [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vzor třídy a struktury. Všechny události v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] jsou na základě knihovny tříd <xref:System.EventHandler> delegáta, který je definován následujícím způsobem:  
  
```csharp  
public delegate void EventHandler(object sender, EventArgs e);  
```  
  
> [!NOTE]
>  [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] Představuje obecné verzi tohoto delegáta <xref:System.EventHandler%601>. Následující příklady ukazují, jak používat obě verze.  
  
 I když událostí v třídách, které definujete, může být založené na libovolného typu platný delegáta, i delegáti, které vrací hodnotu, se obecně doporučuje založit události na [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vzor pomocí <xref:System.EventHandler>, jak je znázorněno v následujícím příkladu.  
  
### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a>Chcete-li publikovat události na základě vzoru obslužná rutina události  
  
1.  (Tento krok přeskočte a přejděte na krok 3a, pokud nemáte odeslat vlastní data s vaší událostí.) Deklarování třídy pro vaše vlastní data v oboru, který je viditelná pro třídy vydavatele a odběratele. Pak přidejte požadované členy pro uložení dat vlastních událostí. V tomto příkladu se vrátí jednoduchým řetězcem.  
  
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
  
2.  (Tento krok přeskočte, pokud používáte obecný verzi <xref:System.EventHandler%601> .) Ve třídě publikování delegáta deklarujte. Zadejte jeho název, který končí *obslužná rutina události*. Druhý parametr určuje vaše vlastní typ EventArgs.  
  
    ```csharp  
    public delegate void CustomEventHandler(object sender, CustomEventArgs a);  
    ```  
  
3.  Deklarace událostí v třídě publikování pomocí jedné z následujících kroků.  
  
    1.  Pokud máte žádné vlastní třídy EventArgs, bude váš typ události delegát neobecnou obslužná rutina události. Nemáte delegáta deklarovat, protože je již deklarována <xref:System> obor názvů, který je součástí při vytváření projektu C#. Přidejte následující kód do vaší třídy vydavatele.  
  
        ```csharp  
        public event EventHandler RaiseCustomEvent;  
        ```  
  
    2.  Pokud používáte verzi neobecnou <xref:System.EventHandler> a máte vlastní třídy odvozené od <xref:System.EventArgs>, deklarování událost v třídě publikování a použití delegáta z kroku 2 jako typ.  
  
        ```csharp  
        public event CustomEventHandler RaiseCustomEvent;  
        ```  
  
    3.  Pokud používáte obecný verze, není nutné vlastní delegáta. Místo toho v třídě publikování zadat typ vašeho událostí jako `EventHandler<CustomEventArgs>`, nahraďte název vlastní třídy mezi lomené závorky.  
  
        ```csharp  
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;  
        ```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje předchozí kroky, pomocí vlastní třídy EventArgs a <xref:System.EventHandler%601> jako typ události.  
  
 [!code-csharp[csProgGuideEvents#2](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-publish-events-that-conform-to-net-framework-guidelines_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Delegate>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Události](../../../csharp/programming-guide/events/index.md)  
 [Delegáti](../../../csharp/programming-guide/delegates/index.md)

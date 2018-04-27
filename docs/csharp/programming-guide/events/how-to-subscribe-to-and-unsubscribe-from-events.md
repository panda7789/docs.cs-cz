---
title: 'Postupy: Přihlášení a odhlášení odběru událostí (Průvodce programováním v C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ecb65a2156f83d9da722329ff6159bb08e464eaa
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Postupy: Přihlášení a odhlášení odběru událostí (Průvodce programováním v C#)
Přihlášení k odběru na událost, která se publikuje jinou třídou, když chcete napsat vlastní kód, který je volána, když se vyvolá tuto událost. Například může přihlásíte k odběru na tlačítko `click` událostí, aby bylo možné aplikaci dělat něco užitečné, když uživatel klikne na tlačítko.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Přihlásit k odběru událostí pomocí prostředí Visual Studio IDE  
  
1.  Pokud nevidíte **vlastnosti** okno v **návrhu** zobrazit, klikněte pravým tlačítkem na formulář nebo ovládací prvek, pro který chcete vytvořit obslužnou rutinu a vyberte **vlastnosti**.  
  
2.  Na **vlastnosti** okně klikněte na tlačítko **události** ikonu.  
  
3.  Dvakrát klikněte na událost, kterou chcete vytvořit, například `Load` událostí.  
  
     Visual C# vytvoří metodu obslužné rutiny události prázdný a přidá ji do vašeho kódu. Případně můžete přidat kód ručně v **kód** zobrazení. Například následující řádky kódu deklarovat metodu obslužné rutiny události, který bude volán při `Form` třídy vyvolá `Load` událostí.  
  
     [!code-csharp[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     Řádek kódu, který je požadován k odběru události je také automaticky generovány v `InitializeComponent` metoda v souboru Form1.Designer.cs ve vašem projektu. Vypadá takto:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Přihlásit k odběru událostí prostřednictvím kódu programu  
  
1.  Definujte metodu obslužné rutiny události, jejichž podpis odpovídá delegáta pro událost. Například, pokud je na základě události <xref:System.EventHandler> se zakázaným inzerováním metoda představuje typ delegáta, následující kód:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  Použít operátor přiřazení sčítání (`+=`) připojit vaší obslužné rutiny události pro událost. V následujícím příkladu se předpokládá, že objekt s názvem `publisher` má událost s názvem `RaiseCustomEvent`. Všimněte si, že třídě odběratele potřebuje odkaz na třídě vydavatele Chcete-li se přihlásit k jeho události odběru.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Všimněte si, že předchozí syntaxe jazyka C# 2.0 nové. Je přesně odpovídá syntaxe jazyka C# 1.0, ve kterém musí být explicitně vytvořen zapouzdřením delegát pomocí `new` – klíčové slovo:  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Obslužné rutiny události lze také přidat pomocí výrazu lambda:  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     Další informace najdete v tématu [postupy: použití Lambda výrazy mimo LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a>Přihlásit k odběru událostí pomocí anonymní metody  
  
-   Pokud nebudete mít k odhlášení odběru událostí později, můžete použít operátor přiřazení sčítání (`+=`) pro připojení anonymní metody k události. V následujícím příkladu se předpokládá, že objekt s názvem `publisher` má událost s názvem `RaiseCustomEvent` a že `CustomEventArgs` třída definována také k provedení nějaký druh informací o specializované události. Všimněte si, že třída odběratele musí odkaz na `publisher` Chcete-li se přihlásit k jeho události odběru.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Je důležité si všimněte si, že nelze zrušíte snadno událost Pokud použijete anonymní funkce si ji předplatili. Chcete-li odhlásit v tomto scénáři, je potřeba přejděte zpět na kód, kde se přihlásíte k odběru události, uložit jako proměnnou delegáta anonymní metody a pak přidejte delegát pro událost. Obecně doporučujeme anonymní funkce nepoužívejte k odběru událostí, pokud bude mít k odhlášení odběru událostí novější někde v kódu. Další informace o anonymní funkce najdete v tématu [anonymní funkce](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Odhlášení  
 Abyste zabránili vaší obslužné rutiny událostí je volána, když událost se vyvolá, odhlášení odběru událostí. Prevence úniků prostředků by měl odhlášení odběru událostí před vyřazení objekt odběratele. Dokud zrušíte událost, vícesměrového vysílání delegát podkladovou události v objektu, publikování obsahuje odkaz na delegáta, který zapouzdřuje obslužné rutiny události odběratele. Tak dlouho, dokud objekt publikování obsahuje tento odkaz, neodstraní uvolňování objektu odběratele.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Chcete-li odhlásit z události  
  
-   Operátor přiřazení odčítání (`-=`) k odhlášení odběru událostí:  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Pokud všechny Odběratelé, kteří mají odhlásil z události, instanci události ve třídě vydavatele je nastavena na `null`.  
  
## <a name="see-also"></a>Viz také  
 [Události](../../../csharp/programming-guide/events/index.md)  
 [event](../../../csharp/language-reference/keywords/event.md)  
 [Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET Framework](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
 [-= – Operátor (referenční dokumentace jazyka C#)](../../language-reference/operators/subtraction-assignment-operator.md)  
 [+= – operátor](../../../csharp/language-reference/operators/addition-assignment-operator.md)
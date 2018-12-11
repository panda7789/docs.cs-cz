---
title: 'Postupy: Přihlaste se k odběru a zrušit její odběr události – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 89647687c73cdb9b81625b830f0c9a77f1c67d13
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241084"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Postupy: Přihlaste se k odběru a zrušit její odběr událostí (C# Průvodce programováním v)
Se přihlásíte k odběru události, která se publikuje jinou třídou, když chcete napsat vlastní kód, který se volá, když se vyvolá tuto událost. Například může přihlásit tlačítko `click` událostí, aby vaše aplikace dělat něco užitečné, když uživatel klikne na tlačítko.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Přihlásit k odběru události pomocí rozhraní IDE sady Visual Studio  
  
1.  Pokud nevidíte **vlastnosti** okno v **návrhu** zobrazení, klikněte pravým tlačítkem na formulář nebo ovládací prvek, pro kterou chcete vytvořit obslužnou rutinu události a vyberte **vlastnosti**.  
  
2.  Nahoře **vlastnosti** okna, klikněte na tlačítko **události** ikonu.  
  
3.  Poklikáním na událost, kterou chcete vytvořit, například `Load` událostí.  
  
     Visual C# vytvoří metodu obslužné rutiny události prázdný a přidá ji do vašeho kódu. Případně můžete přidat ručně v kódu **kód** zobrazení. Například následující řádky kódu deklarovat metodu obslužné rutiny události, která bude volána při `Form` třídy vyvolá `Load` událostí.  
  
     [!code-csharp[csProgGuideEvents#11](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-subscribe-to-and-unsubscribe-from-events_1.cs)]  
  
     Řádek kódu, který je potřeba k události registrovat také automaticky generován `InitializeComponent` metody v souboru Form1.Designer.cs ve vašem projektu. Vypadal takto:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Přihlaste se k odběru událostí prostřednictvím kódu programu  
  
1.  Definujte metodu obslužné rutiny události, jejíž podpis odpovídá delegáta pro událost. Například, pokud je na základě události <xref:System.EventHandler> typu delegátu, následující kód představuje pahýl metody:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2.  Operátor přiřazení sčítání (`+=`) připojit vaše obslužná rutina události pro událost. V následujícím příkladu se předpokládá, že objekt s názvem `publisher` má událost s názvem `RaiseCustomEvent`. Všimněte si, že třída odběratele musí odkaz na třídu vydavatele k přihlášení k odběru jeho událostí.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Všimněte si, že předchozí syntaxi je nového v jazyce C# 2.0. Je přesně odpovídá syntaxe jazyka C# 1.0 ve kterém musí být explicitně vytvořeny zapouzdřující delegáta s použitím `new` – klíčové slovo:  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Pomocí výrazu lambda lze také přidat obslužné rutiny události:  
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        // Use a lambda expression to define an event handler.  
        this.Click += (s,e) => { MessageBox.Show(  
           ((MouseEventArgs)e).Location.ToString());};  
    }  
    ```  
  
     Další informace najdete v tématu [jak: Použití výrazů Lambda mimo LINQ](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-lambda-expressions-outside-linq.md).  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a>Přihlásit k odběru událostí s využitím anonymní metoda  
  
-   Pokud nebudete mít k odhlášení odběru události později, můžete použít operátor přiřazení sčítání (`+=`) na anonymní metodu připojte k této události. V následujícím příkladu se předpokládá, že objekt s názvem `publisher` má událost s názvem `RaiseCustomEvent` a že `CustomEventArgs` třída definována také provádět nějaký druh informací o specializované události. Všimněte si, že třída odběratele musí odkaz na `publisher` k přihlášení k odběru jeho událostí.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Je důležité si všimněte, že je nelze zrušit snadno odběr události byste používali anonymní funkce pro si ji předplatit. Zrušení odběru v tomto scénáři, je nutné přejít zpět do kódu, kde se přihlásíte k odběru události, uložte anonymní metody delegáta proměnné a pak přidat delegáta pro událost. Obecně doporučujeme, abyste je velmi riskantní používat anonymní funkce přihlásit k odběru události v případě, že budete muset zrušit odběr události někdy později ve vašem kódu. Další informace o anonymní funkce, najdete v části [anonymní funkce](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Ruší se předplatné  
 Abyste zabránili vaše obslužná rutina události volaná při vyvolání události, zrušit odběr události. Pokud chcete zabránit nedostatku prostředků by měl zrušit odběr událostí před vyřazení objektu odběratele. Dokud odběr události vícesměrového vysílání delegáta, které je základem událost v objektu publikování obsahuje odkaz na delegáta, který zapouzdřuje obslužná rutina události odběratele. Tak dlouho, dokud publikování objekt obsahuje tento odkaz, nedojde k odstranění objektu odběratele uvolňování paměti.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Chcete-li zrušit odběr události  
  
-   Operátor přiřazení odčítání (`-=`) Chcete-li zrušit odběr události:  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Když všichni předplatitelé odhlásili odběr události, instanci události ve třídě vydavatele se nastaví na `null`.  
  
## <a name="see-also"></a>Viz také

- [Události](../../../csharp/programming-guide/events/index.md)  
- [event](../../../csharp/language-reference/keywords/event.md)  
- [Postupy: Publikování událostí odpovídajících směrnicím rozhraní .NET](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
- [-= – Operátor (referenční dokumentace jazyka C#)](../../language-reference/operators/subtraction-assignment-operator.md)  
- [+= – operátor](../../../csharp/language-reference/operators/addition-assignment-operator.md)
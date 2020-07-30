---
title: Jak se přihlásit k odběru a zrušit odběr událostí – Průvodce programováním v C#
description: Naučte se odebírat a odhlásit odběr událostí. Přihlaste se k odběru událostí pomocí integrovaného vývojového prostředí sady Visual Studio, programově nebo pomocí anonymní metody.
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: f228cc2e4fd719f4d79c56d65aa45b2a3031cba7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302084"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Jak Přihlásit odběr a zrušit odběr událostí (Průvodce programováním v C#)
Přihlásíte se k odběru události, která je publikována jinou třídou, pokud chcete napsat vlastní kód, který je volán při vyvolání události. Například se můžete přihlásit k odběru události tlačítka, aby `click` se vaše aplikace vytvářely co nejužitečnější, když uživatel klikne na tlačítko.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Přihlášení k odběru událostí pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio  
  
1. Pokud se okno **vlastnosti** nezobrazí, klikněte v **návrhovém** zobrazení pravým tlačítkem myši na formulář nebo ovládací prvek, pro který chcete vytvořit obslužnou rutinu události, a vyberte **vlastnosti**.  
  
2. V horní části okna **vlastnosti** klikněte na ikonu **události** .  
  
3. Dvakrát klikněte na událost, kterou chcete vytvořit, například `Load` událost.  
  
     Visual C# vytvoří prázdnou metodu obslužné rutiny události a přidá ji do kódu. Případně můžete kód přidat ručně v zobrazení **kódu** . Například následující řádky kódu deklaruje metodu obslužné rutiny události, která bude volána, když `Form` Třída vyvolá `Load` událost.  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     Řádek kódu, který je vyžadován pro přihlášení k odběru události, je také automaticky vygenerován v `InitializeComponent` metodě v souboru Form1.Designer.cs v projektu. Vypadá takto:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Programové přihlášení k odběru událostí  
  
1. Definujte metodu obslužné rutiny události, jejíž signatura odpovídá signatuře delegáta události. Například pokud je událost založená na <xref:System.EventHandler> typu delegáta, následující kód představuje zástupnou proceduru metody:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. Pomocí operátoru přiřazení sčítání ( `+=` ) připojte k události obslužnou rutinu události. V následujícím příkladu Předpokládejme, že objekt s názvem `publisher` má událost s názvem `RaiseCustomEvent` . Všimněte si, že třída odběratele potřebuje odkaz na třídu vydavatele, aby se přihlásil k odběru jeho událostí.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Všimněte si, že předchozí syntaxe je v C# 2,0 nová. Je přesně stejný jako syntaxe C# 1,0, ve které musí být delegát zapouzdření explicitně vytvořen pomocí `new` klíčového slova:  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     [Výraz lambda](../statements-expressions-operators/lambda-expressions.md) lze také použít k určení obslužné rutiny události:
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        this.Click += (s,e) =>
            {
                MessageBox.Show(((MouseEventArgs)e).Location.ToString());
            };
    }  
    ```  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a>Přihlášení k odběru událostí pomocí anonymní metody  
  
- Pokud se nebudete muset odhlásit k odběru události později, můžete použít operátor přiřazení sčítání ( `+=` ) a k události připojit anonymní metodu. V následujícím příkladu Předpokládejme, že objekt s názvem `publisher` má událost s názvem `RaiseCustomEvent` a že `CustomEventArgs` Třída byla také definována tak, aby provedla určitý druh informací o zvláštních událostech. Všimněte si, že třída odběratele potřebuje odkaz na, aby `publisher` se přihlásil k odběru jeho událostí.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Je důležité si všimnout, že pokud jste k přihlášení k odběru použili anonymní funkci, nemůžete se k odběru události snadno odhlásit. Chcete-li zrušit odběr v tomto scénáři, je nutné přejít zpět na kód, kde jste přihlášeni k odběru události, uložit anonymní metodu do proměnné delegáta a poté přidat delegáta události. Obecně doporučujeme, abyste nepoužívali anonymní funkce pro přihlášení k odběru událostí, pokud budete muset zrušit odběr události v pozdější fázi kódu. Další informace o anonymních funkcích naleznete v tématu [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Probíhá rušení odběru  
 Chcete-li zabránit vyvolání obslužné rutiny události při vyvolání události, odhlaste se od události. Aby nedošlo k nevracení prostředků, měli byste zrušit odběr událostí předtím, než vyřadíte objekt předplatitele. Dokud neprovedete zrušení odběru události, delegát vícesměrového vysílání, který je na události v objektu publikování, odkazuje na delegáta, který zapouzdřuje obslužnou rutinu události odběratele. Pokud objekt publikování obsahuje tento odkaz, uvolňování paměti neodstraní váš objekt předplatitele.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Zrušení odběru události  
  
- K odhlášení odběru události použijte operátor přiřazení odčítání ( `-=` ):  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Když se zruší odběr všech předplatitelů z nějaké události, instance události ve třídě vydavatele je nastavená na `null` .  
  
## <a name="see-also"></a>Viz také:

- [Události](./index.md)
- [událostí](../../language-reference/keywords/event.md)
- [Jak publikovat události, které jsou v souladu s pokyny pro .NET](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [-a-= – operátory](../../language-reference/operators/subtraction-operator.md)
- [+ a + = – operátory](../../language-reference/operators/addition-operator.md)

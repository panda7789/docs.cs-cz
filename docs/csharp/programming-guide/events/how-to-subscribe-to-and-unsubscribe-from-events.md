---
title: Jak se přihlásit k odběru a odhlásit se z událostí - C# Programming Guide
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: 3df357cb15f7f77cefbf360dd9615ce246afe2ea
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705324"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a>Jak se přihlásit k odběru a odhlásit se z událostí (C# Programming Guide)
Přihlášení k odběru události, která je publikována jinou třídou, pokud chcete napsat vlastní kód, který je volán při vyvolání této události. Můžete se například přihlásit k `click` odběru události tlačítka, aby vaše aplikace udělala něco užitečného, když uživatel klikne na tlačítko.  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a>Přihlášení k odběru událostí pomocí ide sady Visual Studio  
  
1. Pokud se v návrhovém **zobrazení** nezobrazí okno **Vlastnosti,** klepněte pravým tlačítkem myši na formulář nebo ovládací prvek, pro který chcete vytvořit obslužnou rutinu události, a vyberte **příkaz Vlastnosti**.  
  
2. V horní části okna **Vlastnosti** klikněte na ikonu **Události.**  
  
3. Poklepejte na událost, kterou chcete vytvořit, například na `Load` událost.  
  
     Visual C# vytvoří metodu obslužné rutiny prázdné události a přidá ji do kódu. Případně můžete přidat kód ručně v zobrazení **kódu.** Například následující řádky kódu deklarují metodu obslužné rutiny události, která bude volána, `Form` když třída vyvolá `Load` událost.  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     Řádek kódu, který je nutný k přihlášení k odběru `InitializeComponent` události, je také automaticky generován v metodě v souboru Form1.Designer.cs v projektu. Podobá se toto:  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a>Chcete-li se přihlásit k odběru událostí programově  
  
1. Definujte metodu obslužné rutiny události, jejíž podpis odpovídá podpisu delegáta pro událost. Například pokud je událost založena <xref:System.EventHandler> na typu delegáta, následující kód představuje zástupný kód metody:  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. Pomocí operátoru přiřazení`+=`sčítání ( ) připojte k události obslužnou rutinu události. V následujícím příkladu předpokládejme, `publisher` že objekt `RaiseCustomEvent`s názvem má událost s názvem . Všimněte si, že třída odběratele potřebuje odkaz na třídu vydavatele, aby se mohla přihlásit k odběru svých událostí.  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     Všimněte si, že předchozí syntaxe je nová v C# 2.0. Je přesně ekvivalentní syntaxi jazyka C# 1.0, ve které musí být encapsulating delegate explicitně vytvořen pomocí klíčového `new` slova:  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     Výraz [lambda](../statements-expressions-operators/lambda-expressions.md) můžete také použít k určení obslužné rutiny události:
  
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
  
- Pokud se nebudete muset odhlásit z odběru události později,`+=`můžete k události připojit anonymní metodu pomocí operátoru přiřazení sčítání ( ). V následujícím příkladu předpokládejme, `publisher` že objekt `RaiseCustomEvent` s `CustomEventArgs` názvem má událost s názvem a že třída byla také definována tak, aby nesla nějaký druh specializovaných informací o událostech. Všimněte si, že třída `publisher` odběratele potřebuje odkaz na k přihlášení k odběru své události.  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     Je důležité si uvědomit, že nemůžete snadno odhlásit z události, pokud jste použili anonymní funkci k odběru. Chcete-li odhlásit v tomto scénáři, je nutné se vrátit ke kódu, kde se přihlásíte k odběru události, uložte anonymní metodu v proměnné delegáta a pak přidejte delegáta k události. Obecně doporučujeme, abyste nepoužívali anonymní funkce k přihlášení k odběru událostí, pokud budete muset odhlásit z události v určitém pozdějším okamžiku vašeho kódu. Další informace o anonymních funkcích naleznete [v tématu Anonymní funkce](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="unsubscribing"></a>Odhlášení  
 Chcete-li zabránit vyvolání obslužné rutiny události při vyvolání události, odhlaste se od události. Chcete-li zabránit úniku prostředků, měli byste zrušit odběr z událostí před vyřazením objektu odběratele. Dokud se neodhlásíte z události, delegát vícesměrového vysílání, který je základem události v objektu publikování, má odkaz na delegáta, který zapouzdřuje obslužnou rutinu události odběratele. Tak dlouho, dokud objekt publikování obsahuje tento odkaz, uvolňování paměti neodstraní objekt odběratele.  
  
#### <a name="to-unsubscribe-from-an-event"></a>Odhlášení z odběru události  
  
- K odhlášení z`-=`události použijte operátor přiřazení odčítání ( ).  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     Pokud se všichni odběratelé odhlásili z události, instance události ve `null`třídě vydavatele je nastavena na .  
  
## <a name="see-also"></a>Viz také

- [Akce](./index.md)
- [Událost](../../language-reference/keywords/event.md)
- [Jak publikovat události vyhovující pravidlům rozhraní .NET Framework](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [- a -= operátoři](../../language-reference/operators/subtraction-operator.md)
- [+ a += operátory](../../language-reference/operators/addition-operator.md)

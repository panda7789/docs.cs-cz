---
title: 'Postupy: Implementace obousměrné komunikace mezi kódem DHTML a kódem klientské aplikace'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.ObjectForScripting
- WebBrowser.Document
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- communications [Windows Forms], DHTML and client applications
- examples [Windows Forms], WebBrowser control
- WebBrowser control [Windows Forms], communication between DHTML and client application
- DHTML [Windows Forms], embedding in Windows Forms
ms.assetid: 55353a32-b09e-4479-a521-ff3a5ff9a708
ms.openlocfilehash: 45df54b3a590078eff6ddc1197db5b0124663cf5
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971921"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a>Postupy: Implementace obousměrné komunikace mezi kódem DHTML a kódem klientské aplikace

Pomocí <xref:System.Windows.Forms.WebBrowser> ovládacího prvku lze přidat existující kód webové aplikace DHTML (Dynamic HTML) do klientských aplikací model Windows Forms. To je užitečné, když jste investovali významnou dobu vývoje při vytváření ovládacích prvků založených na technologii DHTML a chcete využít výhod bohatých funkcí uživatelského rozhraní model Windows Forms bez nutnosti přepsat stávající kód.

Ovládací prvek umožňuje implementovat obousměrnou komunikaci mezi kódem klientské aplikace a kódem skriptu webové stránky <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> prostřednictvím vlastností a <xref:System.Windows.Forms.WebBrowser.Document%2A>. <xref:System.Windows.Forms.WebBrowser> Kromě toho můžete nakonfigurovat <xref:System.Windows.Forms.WebBrowser> ovládací prvek tak, aby vaše webové ovládací prvky byly plynule s dalšími ovládacími prvky ve formuláři aplikace, a tím se skryje jejich implementace DHTML. Chcete-li plynule prolnout ovládací prvky, naformátujte stránku jako zobrazenou tak, aby barva pozadí a vizuální styl odpovídaly zbývající části <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>formuláře <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, a <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> pomocí vlastností, a můžete zakázat standardní funkce prohlížeče.

## <a name="to-embed-dhtml-in-your-windows-forms-application"></a>Vložení DHTML do aplikace model Windows Forms

1. <xref:System.Windows.Forms.WebBrowser> Nastavte <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> vlastnostovládacího`false` prvku na, chcete-li zabránit ovládacímuprvkuvotevíránísouborů,kteréjsounaněj<xref:System.Windows.Forms.WebBrowser> přetaženy.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]

2. Nastavte <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> vlastnost ovládacího prvku na `false` hodnotu, chcete- <xref:System.Windows.Forms.WebBrowser> li zabránit ovládacímu prvku v zobrazení místní nabídky, když na něj uživatel klikne pravým tlačítkem myši.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]

3. Nastavte <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> vlastnost ovládacího prvku na `false` hodnotu, chcete- <xref:System.Windows.Forms.WebBrowser> li zabránit ovládacímu prvku v reakci na klávesové zkratky.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]

4. Nastavte vlastnost v konstruktoru formuláře <xref:System.Windows.Forms.Form.Load> nebo obslužné rutině události. <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A>

     Následující kód používá pro objekt skriptování vlastní třídu Form.

    > [!NOTE]
    >  Objekt modelu COM musí být schopný přistupovat ke skriptovacímu objektu. Chcete-li, aby byl <xref:System.Runtime.InteropServices.ComVisibleAttribute> formulář viditelný pro model COM, přidejte atribut do třídy Form.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]

5. Implementujte veřejné vlastnosti nebo metody v kódu aplikace, který bude používat váš kód skriptu.

     Například pokud použijete třídu Form objektu Script, přidejte do třídy formu následující kód.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]

6. `window.external` Použijte objekt v kódu skriptu pro přístup k veřejným vlastnostem a metodám zadaného objektu.

     Následující kód jazyka HTML ukazuje, jak zavolat metodu na objekt skriptování z kliknutí na tlačítko. Zkopírujte tento kód do prvku tělo dokumentu HTML, který jste načetli pomocí <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody ovládacího prvku nebo přiřadíte <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnosti ovládacího prvku.

    ```html
    <button onclick="window.external.Test('called from script code')">
        call client code from script code
    </button>
    ```

7. Implementujte funkce v kódu skriptu, který bude používat váš kód aplikace.

     Následující prvek skriptu HTML poskytuje ukázkovou funkci. Zkopírujte tento kód do prvku head dokumentu HTML, který jste načetli pomocí <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody ovládacího prvku nebo přiřadíte <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnosti ovládacího prvku.

    ```html
    <script>
    function test(message) {
        alert(message);
    }
    </script>
    ```

8. <xref:System.Windows.Forms.WebBrowser.Document%2A> Použijte vlastnost pro přístup ke kódu skriptu z kódu klientské aplikace.

     Přidejte například následující kód do obslužné rutiny události Button <xref:System.Windows.Forms.Control.Click> .

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]

9. Po dokončení ladění rozšíření DHTML nastavte <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> vlastnost ovládacího prvku na `true` hodnotu, chcete-li zabránit <xref:System.Windows.Forms.WebBrowser> ovládacímu prvku zobrazit chybové zprávy pro problémy s kódem skriptu.

     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]

## <a name="example"></a>Příklad

Následující příklad kompletního kódu poskytuje ukázkovou aplikaci, kterou můžete použít k pochopení této funkce. Kód HTML je načten do <xref:System.Windows.Forms.WebBrowser> ovládacího prvku <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> prostřednictvím vlastnosti namísto načítání z samostatného souboru HTML.

[!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

Tento kód vyžaduje:

- Odkazy na sestavení System a System. Windows. Forms.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>
- [Ovládací prvek WebBrowser](webbrowser-control-windows-forms.md)

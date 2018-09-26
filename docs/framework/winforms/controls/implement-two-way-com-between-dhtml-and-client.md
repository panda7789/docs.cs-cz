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
ms.openlocfilehash: 10b6bb3f55c8acd62101a48ea53b42e331e4210f
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083019"
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a>Postupy: Implementace obousměrné komunikace mezi kódem DHTML a kódem klientské aplikace
Můžete použít <xref:System.Windows.Forms.WebBrowser> ovládacího prvku k přidání existujícího dynamického kódu HTML (DHTML) webové aplikace do klientských aplikací Windows Forms. To je užitečné, když jste investovali významné vývoji při vytváření ovládacích prvků na základě DHTML a budete chtít využít výhod bohaté možnosti uživatelského rozhraní Windows Forms aniž byste museli přepsat existující kód.  
  
 <xref:System.Windows.Forms.WebBrowser> Řízení umožňuje implementace obousměrné komunikace mezi kódem vaší klientské aplikace a webové stránky skriptovací kód prostřednictvím <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> a <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnosti. Kromě toho můžete nakonfigurovat <xref:System.Windows.Forms.WebBrowser> tak, aby vaše webové ovládací prvky bezproblémově prolínat s jinými ovládacími prvky na formuláři aplikace, skrytí jejich DHTML provádění. Bez problémů a přizpůsobte ovládací prvky, formátování stránky zobrazí tak, aby jeho barvu pozadí a vizuální styl odpovídají zbývající části formuláře a použít <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, a <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> vlastnosti, které chcete zakázat funkce standardním prohlížečem.  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a>Chcete-li vložit DHTML v aplikaci Windows Forms  
  
1.  Nastavte <xref:System.Windows.Forms.WebBrowser> ovládacího prvku <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> vlastnost `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládacího prvku z otevírání souborů vyřadit problém napravit.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2.  Nastavit u tohoto prvku <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> vlastnost `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládací prvek zobrazoval jeho místní nabídku, když uživatel klepne pravým tlačítkem ji.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3.  Nastavit u tohoto prvku <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> vlastnost `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládacího prvku v odpovídání na klávesových zkratek.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4.  Nastavte <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> vlastnost v konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.  
  
     Následující kód používá vlastní třídy formuláře pro objekt skriptování.  
  
    > [!NOTE]
    >  Modelu COM (Component Object) musí být schopen získat přístup k objektu skriptování. Chcete-li zviditelnit formuláře do modelu COM, přidejte <xref:System.Runtime.InteropServices.ComVisibleAttribute> atribut do vaší třídy formuláře.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5.  Implementujte veřejné vlastnosti nebo metody v kódu aplikace, který bude používat váš kód skriptu.  
  
     Například pokud používáte třídu formuláře pro objekt skriptování, přidejte následující kód do třídy formuláře.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6.  Použití `window.external` objekt v kódu skriptu pro přístup k veřejné vlastnosti a metody zadaného objektu.  
  
     Následující kód HTML ukazuje, jak volat metodu na objekt skriptování od kliknutí na tlačítko. Zkopírujte tento kód do elementu těla dokumentu HTML, který načtete pomocí ovládacího prvku <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody nebo přiřadit ovládacího prvku <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnost.  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7.  Implementujte funkce ve vašem skriptovacím kódu, který bude používat váš kód aplikace.  
  
     Následující prvek HTML skript obsahuje ukázkovou funkci. Zkopírujte tento kód do elementu HEAD dokumentu HTML, který načtete pomocí ovládacího prvku <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metody nebo přiřadit ovládacího prvku <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnost.  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8.  Použití <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnosti pro přístup k kód skriptu z kódu klienta aplikace.  
  
     Například přidejte následující kód k tlačítku <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. Po dokončení ladění vašeho DHTML nastavit u tohoto prvku <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> vlastnost `true` zabránit <xref:System.Windows.Forms.WebBrowser> ovládací prvek zobrazoval chybové zprávy problémů kód skriptu.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kompletní kód poskytuje ukázkové aplikaci, která vám pomůže pochopit tuto funkci. Kód HTML je načten do <xref:System.Windows.Forms.WebBrowser> řídit prostřednictvím <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnosti namísto načítané z jiného souboru ve formátu HTML.  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento kód vyžaduje:  
  
-   Odkazy na sestavení systému a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>  
 [Ovládací prvek WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)

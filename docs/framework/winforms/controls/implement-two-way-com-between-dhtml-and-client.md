---
title: 'Postupy: Implementace obousměrné komunikace mezi kódem DHTML a kódem klientské aplikace'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f449d026cb3205081fba79e0db87fb04ea3b7211
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-implement-two-way-communication-between-dhtml-code-and-client-application-code"></a>Postupy: Implementace obousměrné komunikace mezi kódem DHTML a kódem klientské aplikace
Můžete použít <xref:System.Windows.Forms.WebBrowser> řízení přidat existující dynamické kódu HTML (DHTML) webové aplikace do aplikace Windows Forms klienta. To je užitečné, když investovaly významné vývoj čas při vytváření ovládacích prvků na základě DHTML a chcete využít výhod možnosti bohaté uživatelské rozhraní Windows Forms bez přepsání existujícího kódu.  
  
 <xref:System.Windows.Forms.WebBrowser> Řízení umožňuje implementace obousměrné komunikace mezi kódem vaší klientské aplikace a webové stránky skriptovací kód prostřednictvím <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> a <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnosti. Kromě toho můžete nakonfigurovat <xref:System.Windows.Forms.WebBrowser> řídit tak, aby vaše ovládací prvky webového bezproblémově s další ovládací prvky ve formuláři aplikace, skrytí DHTML implementace. A bezproblémově přizpůsobte ovládací prvky, formátu stránka zobrazená tak, aby jeho barvu pozadí a vizuální styl odpovídat zbytek formuláře a používat <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>, <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A>, a <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> vlastnosti, které chcete zakázat funkce standardním prohlížečem.  
  
### <a name="to-embed-dhtml-in-your-windows-forms-application"></a>Chcete-li vložit DHTML v aplikaci Windows Forms  
  
1.  Nastavit <xref:System.Windows.Forms.WebBrowser> ovládacího prvku <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> vlastnost, která má `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládací prvek v otevírání souborů, které jsou umístěny na ho.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#1)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#1)]  
  
2.  Nastavte ovládacího prvku <xref:System.Windows.Forms.WebBrowser.IsWebBrowserContextMenuEnabled%2A> vlastnost `false` zabránit <xref:System.Windows.Forms.WebBrowser> řízení zobrazit jeho místní nabídky po kliknutí pravým tlačítkem ji.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#2)]  
  
3.  Nastavte ovládacího prvku <xref:System.Windows.Forms.WebBrowser.WebBrowserShortcutsEnabled%2A> vlastnost `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládací prvek z neodpovídá na požadavky klávesové zkratky.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#3)]  
  
4.  Nastavte <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A> vlastnost v konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.  
  
     Následující kód používá vlastní třídy formuláře pro objekt skriptování.  
  
    > [!NOTE]
    >  Component Object (Model COM) musí být schopni přistupovat objekt skriptování. Ke zviditelnění svého formuláře do modelu COM, přidejte <xref:System.Runtime.InteropServices.ComVisibleAttribute> atributu do vaší třídy formuláře.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#4)]  
  
5.  Veřejné vlastnosti nebo metody implementujte v kódu aplikace, který bude používat váš kód skriptu.  
  
     Například pokud použijete třídy formuláře pro objekt skriptování, přidejte následující kód do vaší třídy formuláře.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#5)]  
  
6.  Použití `window.external` objekt kódu skriptu pro přístup k veřejné vlastnosti a metody zadaného objektu.  
  
     Následující kód HTML ukazuje, jak volat metodu pro skriptovací objekt z klikněte na tlačítko. Zkopírujte tento kód do elementu těla dokumentu HTML, který můžete načíst pomocí ovládacího prvku <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metoda nebo přiřadit ovládacího prvku <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnost.  
  
    ```  
    <button onclick="window.external.Test('called from script code')">  
        call client code from script code  
    </button>  
    ```  
  
7.  Implementace funkce ve vašem kódu skript, který bude používat kódu aplikace.  
  
     Následující element HTML skriptu poskytuje příklad funkce. Zkopírujte tento kód do elementu HEAD dokumentu HTML, který můžete načíst pomocí ovládacího prvku <xref:System.Windows.Forms.WebBrowser.Navigate%2A> metoda nebo přiřadit ovládacího prvku <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnost.  
  
    ```  
    <script>  
    function test(message) {   
        alert(message);   
    }  
    </script>  
    ```  
  
8.  Použití <xref:System.Windows.Forms.WebBrowser.Document%2A> vlastnost, která má přístup k kód skriptu z kódu aplikace klienta.  
  
     Například přidejte následující kód do tlačítko <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#8)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#8)]  
  
9. Po skončení vaší DHTML ladění, nastavte ovládacího prvku <xref:System.Windows.Forms.WebBrowser.ScriptErrorsSuppressed%2A> vlastnost `true` zabránit <xref:System.Windows.Forms.WebBrowser> řízení ze zobrazení chybové zprávy problémů kód skriptu.  
  
     [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#9)]
     [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#9)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu dokončení poskytuje ukázkový aplikace, která můžete použít k pochopení tuto funkci. Kód HTML je načten do <xref:System.Windows.Forms.WebBrowser> ovládat prostřednictvím <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnost místo načítá ze samostatného souboru HTML.  
  
 [!code-csharp[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser.ObjectForScripting#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser.ObjectForScripting/vb/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento kód vyžaduje:  
  
-   Odkazy na systém a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.Document%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.ObjectForScripting%2A?displayProperty=nameWithType>  
 [Ovládací prvek WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)

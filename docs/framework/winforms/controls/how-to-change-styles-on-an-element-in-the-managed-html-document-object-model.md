---
title: 'Postupy: Změna stylů v elementu v modelu spravovaného objektu dokumentu HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM [Windows Forms], changing styles on elements
ms.assetid: 154e8d9f-3e2d-4e8b-a6f3-c85a070e9cc1
ms.openlocfilehash: 9ecb6b90508ca53e3801a633ac2444426e2f8113
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531248"
---
# <a name="how-to-change-styles-on-an-element-in-the-managed-html-document-object-model"></a>Postupy: Změna stylů v elementu v modelu spravovaného objektu dokumentu HTML
Můžete styly řídit vzhled dokumentu a jeho elementy ve formátu HTML. <xref:System.Windows.Forms.HtmlDocument> a <xref:System.Windows.Forms.HtmlElement> podporu <xref:System.Windows.Forms.HtmlElement.Style%2A> vlastnosti, které přijímají řetězce styl následující formát:  
  
 `name1:value1;...;nameN:valueN;`  
  
 Tady je `DIV` s styl řetězec, který nastaví písmo Arial a veškerý text tučně:  
  
 `<DIV style="font-face:arial;font-weight:bold;">`  
  
 `Hello, world!`  
  
 `</DIV>`  
  
 Problém s manipulace s styly pomocí <xref:System.Windows.Forms.HtmlElement.Style%2A> vlastnost je, že může prokázat náročná k přidání a odebrání jednotlivých styl nastavení z řetězce. Například bude nastaveno komplexní postup pro vás k vykreslení předchozí text kurzívou vždy, když uživatel umisťuje kurzor přes `DIV`a proveďte italics vypnout když ukazatel opustí `DIV`. Čas by stát problémem, pokud budete potřebovat k manipulaci s velký počet styly tímto způsobem.  
  
 Následující postup obsahuje kód, který vám pomůže snadno pracovat s stylů na dokumenty HTML a elementy. Postup vyžaduje, že víte, jak provádět základní úkoly ve Windows Forms, jako je vytvoření nového projektu a přidání ovládacího prvku na formulář.  
  
### <a name="to-process-style-changes-in-a-windows-forms-application"></a>Při zpracování změn styl v aplikaci Windows Forms  
  
1.  Vytvoření nového projektu Windows Forms.  
  
2.  Vytvořte nový soubor – třída končící příponou vhodné pro programovací jazyk.  
  
3.  Kopírování `StyleGenerator` do souboru třídy třídy kódu v příkladu části tohoto tématu a uložit kód.  
  
4.  Uložte soubor s názvem Test.htm následující HTML.  
  
    ```  
    <HTML>  
        <BODY>  
  
            <DIV style="font-face:arial;font-weight:bold;">  
                Hello, world!  
            </DIV><P>  
  
            <DIV>  
                Hello again, world!  
            </DIV><P>  
  
        </BODY>  
    </HTML>  
    ```  
  
5.  Přidat <xref:System.Windows.Forms.WebBrowser> ovládací prvek s názvem `webBrowser1` do hlavního formuláře do projektu.  
  
6.  Přidejte následující kód do souboru kódu vašeho projektu.  
  
    > [!IMPORTANT]
    >  Ujistěte se, že `webBrowser1_DocumentCompleted` rutinu událostí je nakonfigurovaný jako naslouchací proces pro <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událostí. V sadě Visual Studio, dvakrát klikněte na <xref:System.Windows.Forms.WebBrowser> řídit, v textovém editoru, nakonfigurujte naslouchací proces prostřednictvím kódu programu.  
  
     [!code-csharp[ManagedDOMStyles#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/Form1.cs#2)]
     [!code-vb[ManagedDOMStyles#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/Form1.vb#2)]  
  
7.  Spusťte projekt. Spustit ukazatelem přes první `DIV` sledovat účinky kódu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje úplného kódu pro `StyleGenerator` třídy, která analyzuje existující hodnoty styl, podporuje přidání, změně a odebrání styly a vrátí novou hodnotu styl s požadované změny.  
  
 [!code-csharp[ManagedDOMStyles#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ManagedDOMStyles/CS/StyleGenerator.cs#1)]
 [!code-vb[ManagedDOMStyles#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ManagedDOMStyles/VB/StyleGenerator.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.HtmlElement>

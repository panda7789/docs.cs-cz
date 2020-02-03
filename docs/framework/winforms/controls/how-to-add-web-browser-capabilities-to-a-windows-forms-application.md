---
title: Přidání možností webového prohlížeče do aplikace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
ms.openlocfilehash: 5feecd975700745541103e81fd09bfc5e788c729
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747223"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Postupy: Přidání schopností webového prohlížeče do aplikace Windows Forms
Pomocí ovládacího prvku <xref:System.Windows.Forms.WebBrowser> můžete do aplikace přidat funkce webového prohlížeče. Ve výchozím nastavení funguje ovládací prvek jako webový prohlížeč. Po načtení počáteční adresy URL nastavením vlastnosti <xref:System.Windows.Forms.WebBrowser.Url%2A> můžete přejít kliknutím na hypertextové odkazy nebo pomocí klávesových zkratek pro přechod zpět a vpřed v historii navigace. Ve výchozím nastavení máte přístup k dalším funkcím prohlížeče pomocí místní nabídky klikněte pravým tlačítkem myši. Nové dokumenty můžete otevřít také tak, že je vyřadíte do ovládacího prvku. Ovládací prvek <xref:System.Windows.Forms.WebBrowser> také obsahuje několik vlastností, metod a událostí, které lze použít k implementaci funkcí uživatelského rozhraní, které jsou podobné těm, které jsou k dispozici v aplikaci Internet Explorer.  
  
 Následující příklad kódu implementuje panel Adresa, typické tlačítka prohlížeče, nabídku **soubor** , stavový řádek a záhlaví, které zobrazuje název aktuální stránky.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení `System`, `System.Drawing`a `System.Windows.Forms`.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.WebBrowser>
- [Ovládací prvek WebBrowser](webbrowser-control-windows-forms.md)

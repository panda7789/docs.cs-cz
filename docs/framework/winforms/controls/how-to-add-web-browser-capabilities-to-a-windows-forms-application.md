---
title: Přidání možností webového prohlížeče do aplikace
description: Naučte se, jak přidat funkce webového prohlížeče do model Windows Forms aplikace s ovládacím prvkem WebBrowser.
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
ms.openlocfilehash: a5a33961ac8301bda86bb5f34e65ac159308987f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174546"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Postup přidání možností webového prohlížeče do aplikace model Windows Forms

Pomocí <xref:System.Windows.Forms.WebBrowser> ovládacího prvku můžete do aplikace přidat funkce webového prohlížeče. Ve výchozím nastavení funguje ovládací prvek jako webový prohlížeč. Po načtení počáteční adresy URL nastavením <xref:System.Windows.Forms.WebBrowser.Url%2A> vlastnosti můžete přejít kliknutím na hypertextové odkazy nebo pomocí klávesových zkratek pro přechod zpět a vpřed v historii navigace. Ve výchozím nastavení máte přístup k dalším funkcím prohlížeče pomocí místní nabídky klikněte pravým tlačítkem myši. Nové dokumenty můžete otevřít také tak, že je vyřadíte do ovládacího prvku. <xref:System.Windows.Forms.WebBrowser>Ovládací prvek má také několik vlastností, metod a událostí, které lze použít k implementaci funkcí uživatelského rozhraní, které jsou podobné těm, které se nachází v aplikaci Internet Explorer.

Následující příklad kódu implementuje panel Adresa, typické tlačítka prohlížeče, nabídku **soubor** , stavový řádek a záhlaví, které zobrazuje název aktuální stránky.

## <a name="example"></a>Příklad

[!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]
  
## <a name="compile-the-code"></a>Kompilovat kód

Tento příklad vyžaduje:

- Odkazy na `System` sestavení, `System.Drawing` a `System.Windows.Forms` .

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.WebBrowser>
- [Ovládací prvek WebBrowser](webbrowser-control-windows-forms.md)

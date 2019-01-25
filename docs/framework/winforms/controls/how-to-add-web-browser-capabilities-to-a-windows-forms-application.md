---
title: 'Postupy: Přidání schopností webového prohlížeče do formulářové aplikaci Windows'
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
ms.openlocfilehash: 0bbfff139d1ba93bc87bf174c1d20dfae65009ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54685149"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Postupy: Přidání schopností webového prohlížeče do formulářové aplikaci Windows
S <xref:System.Windows.Forms.WebBrowser> ovládacího prvku, můžete přidat funkce webového prohlížeče do vaší aplikace. Ovládací prvek funguje jako webového prohlížeče ve výchozím nastavení. Po načtení počáteční adresu URL tak, že nastavíte <xref:System.Windows.Forms.WebBrowser.Url%2A> vlastností, můžete přejít klepnutím na hypertextové odkazy nebo pomocí klávesové zkratky přejít zpět a vpřed mezi historii navigace. Ve výchozím nastavení můžete přístup k funkcím Další prohlížeče prostřednictvím klikněte pravým tlačítkem na nabídku. Můžete také otevřít nové dokumenty přetažením na ovládací prvek. <xref:System.Windows.Forms.WebBrowser> Ovládací prvek má také několik vlastnosti, metody a události, které můžete použít k implementaci funkce uživatelského rozhraní, podobné těm v aplikaci Internet Explorer.  
  
 Následující příklad kódu se implementuje adresním řádku, typické prohlížeče tlačítka, **souboru** nabídka stavového řádku a záhlaví okna, která zobrazí aktuální název stránky.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy `System,``System.Drawing`, a `System.Windows.Forms` sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.WebBrowser>
- [Ovládací prvek WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)

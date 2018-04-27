---
title: 'Postupy: Přidání schopností webového prohlížeče do formulářové aplikace Windows'
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
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fb5809a7932df2950b2badc983adeded1b3f0aa5
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Postupy: Přidání schopností webového prohlížeče do formulářové aplikace Windows
Pomocí <xref:System.Windows.Forms.WebBrowser> ovládací prvek, můžete přidat funkce webového prohlížeče do vaší aplikace. Ve výchozím nastavení funguje jako webový prohlížeč ovládací prvek. Po načtení počáteční adresa URL nastavením <xref:System.Windows.Forms.WebBrowser.Url%2A> vlastnost, můžete přejít kliknutím hypertextových odkazů nebo pomocí klávesové zkratky přesunout zpátky a předávání prostřednictvím historie navigace. Ve výchozím nastavení můžete přístup k funkcím Další prohlížeče prostřednictvím místní nabídce klikněte pravým tlačítkem. Můžete také otevřít nové dokumenty umístěním do ovládacího prvku. <xref:System.Windows.Forms.WebBrowser> Ovládací prvek také obsahuje několik vlastností, metod a události, které můžete použít k implementaci podobné těm, které jsou součástí aplikace Internet Explorer funkce uživatelského rozhraní.  
  
 Následující příklad kódu implementuje panelu Adresa, tlačítka typické prohlížeče, **souboru** nabídky, stavového řádku a záhlaví, která zobrazuje název aktuální stránky.  
  
## <a name="example"></a>Příklad  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazuje na `System,``System.Drawing`, a `System.Windows.Forms` sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.WebBrowser>  
 [Ovládací prvek WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)

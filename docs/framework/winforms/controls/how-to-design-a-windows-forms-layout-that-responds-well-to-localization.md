---
title: 'Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci'
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
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7f35a61c4ef8bbda544e36939fe4986a1017fe31
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci
Vytváření formulářů, které jsou připravené k lokalizované výrazně vývoj rychlosti pro mezinárodní trhy. Můžete použít <xref:System.Windows.Forms.TableLayoutPanel> řízení k implementaci rozložení, které reagují řádně při velikosti ovládacích prvků z důvodu změn v jejich <xref:System.Windows.Forms.Control.Text%2A> hodnot vlastností.  
  
## <a name="example"></a>Příklad  
 Tento formulář ukazuje, jak vytvořit rozložení, které při převede zobrazených řetězcové hodnoty do jiných jazyků úměrně upraví. Tento proces překladu se nazývá *lokalizace*. Další informace najdete v tématu [lokalizace](../../../../docs/standard/globalization-localization/localization.md).  
  
 Rozsáhlá podpora pro tuto úlohu v sadě Visual Studio není k dispozici.  Viz také [návod: vytvoření rozložení, který přizpůsobí poměru pro lokalizaci](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  [Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))  
  
3.  [Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
4.  [Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
5.  [Návod: Provádění obecných úloh pomocí inteligentních značek v ovládacích prvcích Windows Forms](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))  
  
6.  [Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
7.  [Návod: Rozvrhování ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))  
  
8.  [Postupy: lokalizace podporují ve Windows Forms pomocí AutoSize a TableLayoutPanel – ovládací prvek](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))  
  
9. [Návod: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [Lokalizace](../../../../docs/standard/globalization-localization/localization.md)

---
title: "Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 24b281e6e1ab56e2c7387435bf2429e7e107c4b8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Postupy: Nastavení rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel
Ovládací prvky v <xref:System.Windows.Forms.TableLayoutPanel> řízení může mít rozsah sousedících řádků a sloupců.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-span-columns-and-rows"></a>Zabraných sloupců a řádků  
  
1.  Přetáhněte <xref:System.Windows.Forms.TableLayoutPanel> řídit z **sada nástrojů** do formuláře.  
  
2.  Přetažení <xref:System.Windows.Forms.Button> řídit z **sada nástrojů** do levého horního buňky <xref:System.Windows.Forms.TableLayoutPanel> ovládací prvek.  
  
3.  Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **ColumnSpan** vlastnost **2**. Všimněte si, že <xref:System.Windows.Forms.Button> řízení zahrnuje prvním a druhém sloupci.  
  
4.  Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **RowSpan** vlastnost **2**. Všimněte si, že <xref:System.Windows.Forms.Button> řízení zahrnuje prvním a druhém řádku.  
  
5.  Nastavte <xref:System.Windows.Forms.Button> ovládacího prvku **ColumnSpan** vlastnost **1**. Všimněte si, že <xref:System.Windows.Forms.Button> řízení přesune do prvního sloupce a zahrnuje prvním a druhém řádku.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvek TableLayoutPanel](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)

---
title: "Kódování a globalizace Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], lack of Unicode support
- DateTimePicker control [Windows Forms], lack of Unicode support
- TrackBar control [Windows Forms], lack of Unicode support
- ImageList component [Windows Forms], lack of Unicode support
- Unicode [Windows Forms]
- ToolBar control [Windows Forms], lack of Unicode support
- international applications [Windows Forms], character display
- StatusBar control [Windows Forms], lack of Unicode support
- MonthCalendar control [Windows Forms], lack of Unicode support
- international characters
- TabControl control [Windows Forms], lack of Unicode support
- Windows Forms, encoding
- TreeView control [Windows Forms], lack of Unicode support
- ProgressBar control [Windows Forms], Unicode-enabled forms
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f25f4f7206b68e961f3c09a488af643ad5d0a4fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="encoding-and-windows-forms-globalization"></a>Kódování a globalizace Windows Forms
Aplikace Windows Forms jsou zcela kódování Unicode, což znamená, že každý znak je reprezentována jedinečné číslo, bez ohledu na to, jakou platformu, program nebo jazyk. Další informace o kódování Unicode, najdete v článku [Unicode consortium webu](http://www.unicode.org).  
  
## <a name="benefits-of-unicode"></a>Výhody kódování Unicode  
 Příklady výhod formuláře s podporou Unicode schopnost pracovat s skripty, které jsou výhradně kódování Unicode, jako je například Hindská. Kromě toho můžete použít více jazyků na jednoho formuláře. V kódu Unicode jsou všechny znaky dva bajty, aby bylo možné žádné speciální úsilí představují dvoubajtové znaky. Je také možné zapsat jednu sadu kód, který bude fungovat na všech platformách. Jedná se o změnu z předchozích verzí [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], ve které jste měli k zápisu jiný kód pro různé platformy, jako je například systému Windows NT a [!INCLUDE[win98](../../../../includes/win98-md.md)].  
  
 Některé ovládací prvky však nepodporují kódování Unicode v [!INCLUDE[win98](../../../../includes/win98-md.md)] a Windows Millennium Edition. Tyto ovládací prvky, které dědí běžného ovládacího prvku, bude zpracovávat data s Windows znakové stránky, jako [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)]. Tyto ovládací prvky jsou: <xref:System.Windows.Forms.TabControl>, <xref:System.Windows.Forms.ListView>, <xref:System.Windows.Forms.TreeView>, <xref:System.Windows.Forms.DateTimePicker>, <xref:System.Windows.Forms.MonthCalendar>, <xref:System.Windows.Forms.TrackBar>, <xref:System.Windows.Forms.ProgressBar>, <xref:System.Windows.Forms.ImageList>, <xref:System.Windows.Forms.ToolBar>, a <xref:System.Windows.Forms.StatusBar>. V důsledku toho nelze zobrazit Unicode data v těchto ovládacích prvků v uvedených platformách. Například nelze zobrazit japonské znaky v angličtině [!INCLUDE[win98](../../../../includes/win98-md.md)] operačního systému.  
  
 Kódování Unicode alternativy k <xref:System.Windows.Forms.ToolBar> a <xref:System.Windows.Forms.StatusBar> ovládacích prvků, použijte <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.StatusStrip> ovládací prvky, které nahradí tyto starší ovládací prvky. Chcete-li udržovat podobné vzhled a chování mezi vizuální prvky v aplikaci, použijte <xref:System.Windows.Forms.MenuStrip> řízení pro vykreslování nabídky místo <xref:System.Windows.Forms.MainMenu>. Jako <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.StatusStrip>, <xref:System.Windows.Forms.MenuStrip> může také zpracovat a zobrazit znaky znakové sady Unicode.  
  
## <a name="see-also"></a>Viz také  
 [Globalizace modelu Windows Forms](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)

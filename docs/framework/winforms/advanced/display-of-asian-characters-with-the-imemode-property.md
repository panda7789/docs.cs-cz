---
title: "Zobrazení asijských znaků s vlastností ImeMode"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Asian languages [Windows Forms], displaying with ImeMode
- Chinese characters [Windows Forms], displaying with ImeMode
- IME mode
- Japanese characters [Windows Forms], displaying with ImeMode
- international applications [Windows Forms], character display
- international characters
- Korean characters
- Asian languages
- Input Method Editor (IME), mode
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5971fd9a75f936d2ec63eea6a086c681ec996652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a>Zobrazení asijských znaků s vlastností ImeMode
<xref:System.Windows.Forms.Control.ImeMode%2A> Vlastnost je používána formuláře a ovládací prvky můžete vynutit konkrétní režim pro editor IME (IME). Editor IME je základní součástí pro psaní skriptů čínština, japonština nebo korejština, protože tyto systémy zápisu obsahují více znaků, než může být zakódován pro běžnou klávesnici. Chcete třeba povolit jenom znaky ASCII v konkrétní textové pole. V takovém případě můžete nastavit <xref:System.Windows.Forms.Control.ImeMode%2A> vlastnost <xref:System.Windows.Forms.ImeMode> a jenom uživatelé budou moci pro tuto konkrétní textového pole zadejte znaky ASCII. Výchozí hodnota <xref:System.Windows.Forms.Control.ImeMode%2A> vlastnost je <xref:System.Windows.Forms.ImeMode>, takže pokud nastavíte vlastnost pro formulář, zdědí všechny ovládací prvky na formuláři tohoto nastavení. Další informace najdete v tématu <xref:System.Windows.Forms.Control.ImeMode%2A> ) a <xref:System.Windows.Forms.ImeMode>.  
  
## <a name="see-also"></a>Viz také  
 [Globalizace modelu Windows Forms](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)

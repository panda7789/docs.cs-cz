---
title: Zobrazení asijských znaků s vlastností ImeMode
ms.date: 03/30/2017
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
ms.openlocfilehash: d3733f642d4218c851040582ee5637b5486a7804
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208453"
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a>Zobrazení asijských znaků s vlastností ImeMode
<xref:System.Windows.Forms.Control.ImeMode%2A> Vlastnost je používána formuláře a ovládací prvky můžete vynutit konkrétní režim pro editor IME (IME). Editor IME je základní součástí pro psaní skriptů čínština, japonština nebo korejština, protože tyto systémy zápisu obsahují více znaků, než může být zakódován pro běžnou klávesnici. Chcete třeba povolit jenom znaky ASCII v konkrétní textové pole. V takovém případě můžete nastavit <xref:System.Windows.Forms.Control.ImeMode%2A> vlastnost <xref:System.Windows.Forms.ImeMode> a jenom uživatelé budou moci pro tuto konkrétní textového pole zadejte znaky ASCII. Výchozí hodnota <xref:System.Windows.Forms.Control.ImeMode%2A> vlastnost je <xref:System.Windows.Forms.ImeMode>, takže pokud nastavíte vlastnost pro formulář, zdědí všechny ovládací prvky na formuláři tohoto nastavení. Další informace najdete v tématu <xref:System.Windows.Forms.Control.ImeMode%2A> ) a <xref:System.Windows.Forms.ImeMode>.  
  
## <a name="see-also"></a>Viz také:

[Globalizace aplikací Windows Forms](globalizing-windows-forms.md)

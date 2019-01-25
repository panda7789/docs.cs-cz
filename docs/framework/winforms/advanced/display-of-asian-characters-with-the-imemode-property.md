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
ms.openlocfilehash: 25602e1a878443bd54411dfd6481581abebda5c7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500516"
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a>Zobrazení asijských znaků s vlastností ImeMode
<xref:System.Windows.Forms.Control.ImeMode%2A> Vlastnost používá formuláře a ovládací prvky vynutit konkrétní režim pro editor IME (IME). Editor IME je nezbytné součásti pro psaní skriptů čínštiny, japonštiny a korejštiny, protože tyto systémy zápisu mít více znaků, než může být zakódován regulární klávesnice. Chcete například povolit pouze znaky ASCII v konkrétní textové pole. V takovém případě můžete nastavit <xref:System.Windows.Forms.Control.ImeMode%2A> vlastnost <xref:System.Windows.Forms.ImeMode> a uživatelé budou moct jenom pro tento konkrétní textového pole zadejte znaky ASCII. Výchozí hodnota <xref:System.Windows.Forms.Control.ImeMode%2A> vlastnost <xref:System.Windows.Forms.ImeMode>, takže pokud jste nastavili vlastnost formuláře, všechny ovládací prvky ve formuláři zdědí toto nastavení. Další informace najdete v tématu <xref:System.Windows.Forms.Control.ImeMode%2A> ) a <xref:System.Windows.Forms.ImeMode>.  
  
## <a name="see-also"></a>Viz také:

- [Globalizace aplikací Windows Forms](globalizing-windows-forms.md)

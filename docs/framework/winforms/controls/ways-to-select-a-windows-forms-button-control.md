---
title: Způsoby výběru ovládacího prvku tlačítko
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: 145166d182f1ec51068ab3e0c23c12b471b69231
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740014"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>Metody výběru ovládacího prvku Windows Forms Button
Tlačítko model Windows Forms může být vybráno následujícími způsoby:  
  
- Pomocí myši klikněte na tlačítko.  
  
- Vyvolá událost <xref:System.Windows.Forms.Control.Click> tlačítka v kódu.  
  
- Přesuňte fokus na tlačítko tak, že stisknete klávesu TAB a kliknete na tlačítko stisknutím klávesy MEZERNÍK nebo ZADÁNÍm příkazu.  
  
- Stiskněte přístupové klávesy (ALT + podtržené písmeno) pro tlačítko. Další informace o přístupových klíčích najdete v tématu [Postupy: vytváření přístupových klíčů pro ovládací prvky model Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).  
  
- Pokud je tlačítko "přijmout" na formuláři, stiskněte klávesu ENTER, a to i v případě, že je vybrán jiný ovládací prvek – s výjimkou případu, kdy je tento jiný ovládací prvek další tlačítko, víceřádkové textové pole nebo vlastní ovládací prvek, který provádí soutisk klíče ENTER.  
  
- Pokud je tlačítko tlačítkem zrušit ve formuláři, stisknutí klávesy ESC zvolí tlačítko, a to i v případě, že je vybrán jiný ovládací prvek.  
  
- Chcete-li vybrat tlačítko programově, zavolejte metodu <xref:System.Windows.Forms.Button.PerformClick%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku Button](button-control-overview-windows-forms.md)
- [Postupy: Reakce na kliknutí na tlačítko Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Ovládací prvek Button](button-control-windows-forms.md)

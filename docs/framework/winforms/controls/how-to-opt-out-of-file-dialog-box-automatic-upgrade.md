---
title: 'Postupy: Zamítnutí automatického upgradu dialogového okna souboru'
ms.date: 03/30/2017
helpviewer_keywords:
- OpenFileDialog [Windows Forms], opt out of automatic upgrade
- file dialog box [Windows Forms], opt out of automatic upgrade
- Windows Vista file dialog box [Windows Forms], opt out of automatic upgrade
- SaveFileDialog [Windows Forms], opt out of automatic upgrade
- AutoUpgradeEnabled property
ms.assetid: 522e482e-cc01-48b1-8d59-9617dc2c4ac1
ms.openlocfilehash: 6fd34e1127747739423f6402f128194a3a39f5e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089143"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Postupy: Zamítnutí automatického upgradu dialogového okna souboru
Když <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> třídy se používají v aplikaci, jejich vzhled a chování závisí na verzi aplikace běží na Windows. Když aplikaci, která byla vytvořena na [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] nebo dřívější se zobrazí na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> se automaticky zobrazí se [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] vzhled a chování. Počínaje [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], můžete zrušit automatický upgrade pro zobrazení <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> s [!INCLUDE[winxp](../../../../includes/winxp-md.md)]– styl vzhledu a chování.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Chcete-li vyjádřit výslovný nesouhlas souboru dialogové okno automatického upgradu  
  
1.  Nastavte <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> vlastnost <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog> k `false` před zobrazení dialogového okna.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FileDialog>

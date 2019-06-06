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
ms.openlocfilehash: e12134768d41589dedbeb5a00cab4244c7324f97
ms.sourcegitcommit: 90f0bee0e8a416e45c78fa3ad4c91ef00e5228d5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2019
ms.locfileid: "66722623"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Postupy: Zamítnutí automatického upgradu dialogového okna souboru
Když <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> třídy se používají v aplikaci, jejich vzhled a chování závisí na verzi aplikace běží na Windows. Když aplikaci, která byla vytvořena na [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] nebo dřívější se zobrazí na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> se automaticky zobrazí se [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] vzhled a chování. Spuštění v rozhraní .NET Framework 3.0, můžete zrušit automatický upgrade pro zobrazení <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> s [!INCLUDE[winxp](../../../../includes/winxp-md.md)]– styl vzhledu a chování.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Chcete-li vyjádřit výslovný nesouhlas souboru dialogové okno automatického upgradu  
  
1. Nastavte <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> vlastnost <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog> k `false` před zobrazení dialogového okna.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FileDialog>

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
ms.openlocfilehash: bbde260cc7f05226c9b06325b45708e1cde3cf8c
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976886"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Postupy: Zamítnutí automatického upgradu dialogového okna souboru
Pokud jsou v aplikaci použity třídy <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog>, jejich vzhled a chování závisí na verzi systému Windows, ve které je aplikace spuštěna. Pokud se v systému Windows Vista zobrazí aplikace vytvořená v .NET Framework 2,0 nebo starší, <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> se automaticky zobrazí s vzhledem a chováním systému Windows Vista. Počínaje .NET Framework 3,0 se můžete odhlásit z automatického upgradu, aby se zobrazila <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> vzhled a chování ve stylu [!INCLUDE[winxp](../../../../includes/winxp-md.md)].  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Automatický upgrade při odhlášení z dialogového okna souboru  
  
1. Před zobrazením dialogového okna nastavte vlastnost <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog> na `false`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FileDialog>

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
ms.openlocfilehash: 154953680426f98a9506feb0b8f4de25c873b795
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959679"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Postupy: Zamítnutí automatického upgradu dialogového okna souboru
Pokud jsou v aplikaci použity třídy <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog>, jejich vzhled a chování závisí na verzi systému Windows, ve které je aplikace spuštěna. Pokud se v systému Windows Vista zobrazí aplikace vytvořená v .NET Framework 2,0 nebo starší, <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> se automaticky zobrazí s vzhledem a chováním systému Windows Vista. Počínaje .NET Framework 3,0 se můžete odhlásit z automatického upgradu a zobrazit <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> s vzhledem a chováním ve stylu systému Windows XP.  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a>Automatický upgrade při odhlášení z dialogového okna souboru  
  
1. Před zobrazením dialogového okna nastavte vlastnost <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog> na `false`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FileDialog>

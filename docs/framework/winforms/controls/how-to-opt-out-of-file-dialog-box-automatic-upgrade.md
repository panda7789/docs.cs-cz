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
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="2b7ed-102">Postupy: Zamítnutí automatického upgradu dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="2b7ed-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="2b7ed-103">Pokud jsou v aplikaci použity třídy <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog>, jejich vzhled a chování závisí na verzi systému Windows, ve které je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="2b7ed-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="2b7ed-104">Pokud se v systému Windows Vista zobrazí aplikace vytvořená v .NET Framework 2,0 nebo starší, <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> se automaticky zobrazí s vzhledem a chováním systému Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="2b7ed-104">When an application that was created on the .NET Framework 2.0 or earlier is displayed on Windows Vista, <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the Windows Vista appearance and behavior.</span></span> <span data-ttu-id="2b7ed-105">Počínaje .NET Framework 3,0 se můžete odhlásit z automatického upgradu, aby se zobrazila <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> vzhled a chování ve stylu [!INCLUDE[winxp](../../../../includes/winxp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b7ed-105">Starting in the .NET Framework 3.0, you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="2b7ed-106">Automatický upgrade při odhlášení z dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="2b7ed-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1. <span data-ttu-id="2b7ed-107">Před zobrazením dialogového okna nastavte vlastnost <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog> na `false`.</span><span class="sxs-lookup"><span data-stu-id="2b7ed-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b7ed-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b7ed-108">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>

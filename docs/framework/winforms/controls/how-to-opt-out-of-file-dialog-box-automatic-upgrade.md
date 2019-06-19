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
ms.openlocfilehash: 0753873ac37f26d6503397290ef4603702737a86
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170618"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="91112-102">Postupy: Zamítnutí automatického upgradu dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="91112-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="91112-103">Když <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> třídy se používají v aplikaci, jejich vzhled a chování závisí na verzi aplikace běží na Windows.</span><span class="sxs-lookup"><span data-stu-id="91112-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="91112-104">Když se zobrazí aplikace, která byla vytvořena na rozhraní .NET Framework 2.0 nebo starší na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> se automaticky zobrazí se [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] vzhled a chování.</span><span class="sxs-lookup"><span data-stu-id="91112-104">When an application that was created on the .NET Framework 2.0 or earlier is displayed on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] appearance and behavior.</span></span> <span data-ttu-id="91112-105">Spuštění v rozhraní .NET Framework 3.0, můžete zrušit automatický upgrade pro zobrazení <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> s [!INCLUDE[winxp](../../../../includes/winxp-md.md)]– styl vzhledu a chování.</span><span class="sxs-lookup"><span data-stu-id="91112-105">Starting in the .NET Framework 3.0, you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="91112-106">Chcete-li vyjádřit výslovný nesouhlas souboru dialogové okno automatického upgradu</span><span class="sxs-lookup"><span data-stu-id="91112-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1. <span data-ttu-id="91112-107">Nastavte <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> vlastnost <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog> k `false` před zobrazení dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="91112-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91112-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91112-108">See also</span></span>

- <xref:System.Windows.Forms.FileDialog>

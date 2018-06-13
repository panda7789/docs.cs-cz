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
ms.openlocfilehash: 380f8abe502c37e57207c43696158c1e3bdc7697
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532484"
---
# <a name="how-to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="f5b26-102">Postupy: Zamítnutí automatického upgradu dialogového okna souboru</span><span class="sxs-lookup"><span data-stu-id="f5b26-102">How To: Opt Out of File Dialog Box Automatic Upgrade</span></span>
<span data-ttu-id="f5b26-103">Když <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> třídy jsou používané v aplikaci, jejich vzhled a chování závisí na verzi aplikace běží na systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f5b26-103">When the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> classes are used in an application, their appearance and behavior depend on the version of Windows the application is running on.</span></span> <span data-ttu-id="f5b26-104">Pokud aplikace, která byla vytvořena na [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] nebo dřívější se zobrazí na [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> se automaticky zobrazí s [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] vzhled a chování.</span><span class="sxs-lookup"><span data-stu-id="f5b26-104">When an application that was created on the [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] or earlier is displayed on [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)], <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> are automatically displayed with the [!INCLUDE[wiprlhext](../../../../includes/wiprlhext-md.md)] appearance and behavior.</span></span> <span data-ttu-id="f5b26-105">Počínaje [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], můžete zamítnutí automatického upgradu zobrazíte <xref:System.Windows.Forms.OpenFileDialog> a <xref:System.Windows.Forms.SaveFileDialog> s [!INCLUDE[winxp](../../../../includes/winxp-md.md)]– styl vzhledu a chování.</span><span class="sxs-lookup"><span data-stu-id="f5b26-105">Starting in the [!INCLUDE[net_v30_short](../../../../includes/net-v30-short-md.md)], you can opt out of the automatic upgrade to display the <xref:System.Windows.Forms.OpenFileDialog> and <xref:System.Windows.Forms.SaveFileDialog> with a [!INCLUDE[winxp](../../../../includes/winxp-md.md)]-style appearance and behavior.</span></span>  
  
### <a name="to-opt-out-of-file-dialog-box-automatic-upgrade"></a><span data-ttu-id="f5b26-106">Pro vyjádření výslovného nesouhlasu souboru dialogové okno automatického upgradu</span><span class="sxs-lookup"><span data-stu-id="f5b26-106">To opt out of file dialog box automatic upgrade</span></span>  
  
1.  <span data-ttu-id="f5b26-107">Nastavte <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> vlastnost <xref:System.Windows.Forms.OpenFileDialog> nebo <xref:System.Windows.Forms.SaveFileDialog> k `false` před zobrazení dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="f5b26-107">Set the <xref:System.Windows.Forms.FileDialog.AutoUpgradeEnabled%2A> property of <xref:System.Windows.Forms.OpenFileDialog> or <xref:System.Windows.Forms.SaveFileDialog> to `false` before you display the dialog box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b26-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5b26-108">See Also</span></span>  
 <xref:System.Windows.Forms.FileDialog>

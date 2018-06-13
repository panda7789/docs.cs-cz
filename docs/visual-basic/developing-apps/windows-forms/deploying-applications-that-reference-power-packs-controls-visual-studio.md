---
title: Nasazení aplikací odkazujících na ovládací prvky Power Pack (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
ms.openlocfilehash: bd235bc0b4a7f9978333931ae1dce012c0950374
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587502"
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>Nasazení aplikací odkazujících na ovládací prvky Power Pack (Visual Studio)
Pokud chcete nasadit aplikaci, která odkazuje na ovládací prvky Power Pack (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, nebo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), ovládací prvky, musí být nainstalován v cílovém počítači.  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>Instalace ovládací prvky Power Pack jako předpoklad  
 Pokud chcete úspěšně nasadit aplikaci, musíte také nasadit všechny součásti, které jsou odkazovány pomocí aplikace. Proces instalace požadovaných součástí se označuje jako *zavádění*.  
  
 Při instalaci sady Visual Studio ve svém vývojovém počítači balíček zaváděcího nástroje Power Pack bude přidán k adresáři zaváděcího nástroje Visual Studio. Tento balíček je k dispozici v případě postupujte podle pokynů pro přidání předpokladů pro buď [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] nebo instalační služba systému Windows.  
  
 Ve výchozím nastavení jsou zaváděné součásti nasazeny ze stejného umístění jako instalační balíček. Alternativně můžete nainstalovat komponenty z adresy URL nebo sdíleného umístění, ze kterého mohou uživatelé stáhnout je podle potřeby.  
  
> [!NOTE]
>  K instalaci samozaváděcí komponenty, může uživatel potřebovat oprávnění pro správu nebo podobné uživatele v počítači. Pro [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikace, to znamená, že bude uživatel potřebovat oprávnění správce k instalaci aplikace, bez ohledu na úroveň zabezpečení, který je určený aplikací. Po instalaci aplikace, může uživatel spustit aplikaci bez oprávnění správce.  
  
 Během instalace uživatelům se zobrazí výzva k instalaci ovládací prvky Power Pack, pokud se nenachází v cílovém počítači.  
  
 Jako alternativu k zavedení spouštěcího programu můžete předem nasadit ovládací prvky Power Pack pomocí systém distribuce elektronické softwaru jako je například Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Instalace předpokladů s aplikací ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Ovládací prvky Power Pack jazyka Visual Basic](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)

---
title: Nasazení aplikací odkazujících na ovládací prvky Power Pack (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
ms.openlocfilehash: bd235bc0b4a7f9978333931ae1dce012c0950374
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198225"
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>Nasazení aplikací odkazujících na ovládací prvky Power Pack (Visual Studio)
Pokud chcete nasadit aplikaci, která odkazuje na ovládací prvky Power Packs (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, nebo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), ovládací prvky musí být nainstalován v cílovém počítači.  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>Jako předpoklad instalace ovládací prvky Power Packs  
 K úspěšnému nasazení aplikace, je nutné nasadit také všechny součásti, které se příslušná aplikace odkazuje. Proces instalace požadovaných součástí se označuje jako *spuštění*.  
  
 Při instalaci sady Visual Studio na svém vývojovém počítači, se přidá balíček zaváděcího nástroje Power Pack do adresáře zaváděcího nástroje sady Visual Studio. Tento balíček bude k dispozici, pokud dodržíte postupy pro přidání požadavky pro buď [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] nebo nasazení Instalační služby systému Windows.  
  
 Ve výchozím nastavení se nasazují se spustil součásti ze stejného umístění jako instalační balíček. Alternativně můžete nasadit komponenty z adresy URL nebo sdíleného umístění, ze kterého uživatelé si je stáhnout podle potřeby.  
  
> [!NOTE]
>  K instalaci součásti se spustil, uživatel může být nutné oprávnění správce nebo podobné uživatele v počítači. Pro [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikací, to znamená, že uživatel bude potřebovat oprávnění správce k instalaci aplikace bez ohledu na úroveň zabezpečení, která je určená aplikací. Po nainstalování aplikace uživatel můžete spustit aplikaci bez oprávnění správce.  
  
 Během instalace uživatelům se výzva k instalaci ovládací prvky Power Packs, pokud nejsou k dispozici na cílovém počítači.  
  
 Jako alternativu k spuštění můžete předem nasadit ovládací prvky Power Packs použití systému distribuční elektronické softwaru jako je například Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Viz také:  
 [Postupy: Instalace předpokladů s aplikací ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Ovládací prvky jazyka Visual Basic Power Pack](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)

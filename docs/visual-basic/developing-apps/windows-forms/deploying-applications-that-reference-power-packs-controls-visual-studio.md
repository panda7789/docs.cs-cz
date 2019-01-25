---
title: Nasazení aplikací odkazujících na ovládací prvky Power Pack (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
ms.openlocfilehash: 3fd46a6e8aad61d2f8ce5a230c856470f913d0bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54551771"
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
- [Postupy: Instalace nezbytných součástí aplikace ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)
- [Visual Basic Power Packs Controls](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)

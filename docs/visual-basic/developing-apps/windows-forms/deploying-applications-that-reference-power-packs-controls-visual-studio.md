---
title: "Nasazení aplikací odkazujících na ovládací prvky Power Pack (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Power Packs, deploying
ms.assetid: f2230f53-a745-4731-89e6-033943faa209
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2a9562acf05cd27eed7bc1ad963845af9a7ca5f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="deploying-applications-that-reference-power-packs-controls-visual-studio"></a>Nasazení aplikací odkazujících na ovládací prvky Power Pack (Visual Studio)
Pokud chcete nasadit aplikaci, která odkazuje na ovládací prvky Power Pack (<xref:Microsoft.VisualBasic.PowerPacks.LineShape>, <xref:Microsoft.VisualBasic.PowerPacks.OvalShape>, <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape>, nebo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>), ovládací prvky, musí být nainstalován v cílovém počítači.  
  
## <a name="installing-the-power-packs-controls-as-a-prerequisite"></a>Instalace ovládací prvky Power Pack jako předpoklad  
 Pokud chcete úspěšně nasadit aplikaci, musíte také nasadit všechny součásti, které jsou odkazovány pomocí aplikace. Proces instalace požadovaných součástí se označuje jako *zavádění*.  
  
 Když [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] je nainstalován ve svém vývojovém počítači, Power Pack balíček zaváděcího nástroje je přidán do [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] adresáře zaváděcího nástroje. Tento balíček je k dispozici v případě postupujte podle pokynů pro přidání předpokladů pro buď [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] nebo instalační služba systému Windows.  
  
 Ve výchozím nastavení jsou zaváděné součásti nasazeny ze stejného umístění jako instalační balíček. Alternativně můžete nainstalovat komponenty z adresy URL nebo sdíleného umístění, ze kterého mohou uživatelé stáhnout je podle potřeby.  
  
> [!NOTE]
>  K instalaci samozaváděcí komponenty, může uživatel potřebovat oprávnění pro správu nebo podobné uživatele v počítači. Pro [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikace, to znamená, že bude uživatel potřebovat oprávnění správce k instalaci aplikace, bez ohledu na úroveň zabezpečení, který je určený aplikací. Po instalaci aplikace, může uživatel spustit aplikaci bez oprávnění správce.  
  
 Během instalace uživatelům se zobrazí výzva k instalaci ovládací prvky Power Pack, pokud se nenachází v cílovém počítači.  
  
 Jako alternativu k zavedení spouštěcího programu můžete předem nasadit ovládací prvky Power Pack pomocí systém distribuce elektronické softwaru jako je například Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: instalace předpokladů s aplikací ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Ovládací prvky Power Pack jazyka Visual Basic](../../../visual-basic/developing-apps/windows-forms/power-packs-controls.md)

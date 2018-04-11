---
title: Nasazení aplikací odkazujících na součást PrintForm (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- PrintForm component [Visual Basic], deploying
ms.assetid: b595ea44-a712-4625-a761-190c64f59bbe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 15b6e21e769c90e23e66e4f87b37f74462423985
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/10/2018
---
# <a name="deploying-applications-that-reference-the-printform-component-visual-basic"></a>Nasazení aplikací odkazujících na součást PrintForm (Visual Basic)
Pokud chcete nasadit aplikaci, která odkazuje <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti, součásti musí být nainstalován v cílovém počítači.  
  
 Ovládací prvky PowerPack jsou již zahrnuty v sadě Visual Studio, ale si můžete stáhnout z [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).  
  
## <a name="installing-the-printform-as-a-prerequisite"></a>Předpokladem je instalace PrintForm  
 Pokud chcete úspěšně nasadit aplikaci, musíte také nasadit všechny součásti, které jsou odkazovány pomocí aplikace. Proces instalace požadovaných součástí se označuje jako *zavádění*.  
  
 Když <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> ve svém vývojovém počítači je nainstalována součást, balíček zaváděcího nástroje sady Microsoft Visual Basic Power Pack se přidá do [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] adresáře zaváděcího nástroje. Tento balíček je k dispozici v případě postupujte podle pokynů pro přidání předpokladů pro buď [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] nebo instalační služba systému Windows.  
  
 Ve výchozím nastavení jsou zaváděné součásti nasazeny ze stejného umístění jako instalační balíček. Alternativně můžete nainstalovat komponenty z adresy URL nebo sdíleného umístění, ze kterého mohou uživatelé stáhnout je podle potřeby.  
  
> [!NOTE]
>  K instalaci samozaváděcí komponenty, může uživatel potřebovat oprávnění pro správu nebo podobné uživatele v počítači. Pro [!INCLUDE[ndptecclick](~/includes/ndptecclick-md.md)] aplikace, to znamená, že bude uživatel potřebovat oprávnění správce k instalaci aplikace, bez ohledu na úroveň zabezpečení, který je určený aplikací. Po instalaci aplikace, může uživatel spustit aplikaci bez oprávnění správce.  
  
 Během instalace, uživatelům se zobrazí výzva k instalaci <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti, pokud není přítomen v cílovém počítači.  
  
 Jako alternativu k zavedení spouštěcího programu, můžete předem nasadit <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> součásti pomocí systému distribuce elektronického software jako Microsoft Systems Management Server.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Instalace předpokladů s aplikací ClickOnce](/visualstudio/deployment/how-to-install-prerequisites-with-a-clickonce-application)  
 [Komponenta PrintForm](../../../visual-basic/developing-apps/printing/printform-component.md)

---
title: "Přehled zabezpečení automatizace uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: ee3847164ecdc9b9868d806b5a1394ffca0bbd31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ui-automation-security-overview"></a>Přehled zabezpečení automatizace uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Tento přehled popisuje model zabezpečení pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] v [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].  
  
<a name="User_Account_Control"></a>   
## <a name="user-account-control"></a>řízení uživatelských účtů  
 Zabezpečení je hlavní fokus [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] a mezi inovace přístup je schopnost uživatelům spustit jako standardní uživatelé (bez oprávnění správce) bez nutně se blokovat spouštění aplikací a služeb, které vyžadují vyšší oprávnění.  
  
 V [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)], většina aplikací se dodává s standard nebo token pro správu. Pokud aplikace nemůže být identifikován jako aplikace pro správu, se spustí jako u standardní aplikace ve výchozím nastavení. Předtím, než aplikace identifikovat jako správce může být spuštěn, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] zobrazí výzvu k souhlasu, a spusťte aplikaci jako zvýšených oprávnění. Řádku souhlasu se zobrazí ve výchozím nastavení, i pokud je uživatel členem místní skupiny Administrators, protože správce spustit jako standardní uživatelé, dokud aplikace nebo součást systému, který vyžaduje pověření správce požádá o oprávnění ke spuštění.  
  
<a name="Tasks_Requiring_Higher_Privileges"></a>   
## <a name="tasks-requiring-higher-privileges"></a>Úlohy, které vyžadují vyšší oprávnění  
 Když se uživatel pokusí provést úlohu, která vyžaduje oprávnění správce, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] uvede dialogové okno s dotazem uživatele o souhlas s pokračovat. Toto dialogové okno je chráněný před komunikaci mezi procesy, tak, aby škodlivého softwaru nejde simulovat vstup uživatele. Podobně nelze na obrazovce přihlášení k ploše přistupovat normálně jinými procesy.  
  
 Klienti automatizace uživatelského rozhraní musí komunikovat s jinými procesy, některé z nich pravděpodobně spuštěná na vyšší úrovni oprávnění. Klienti také může potřebovat přístup k systému dialogových oken, které nejsou standardně viditelné pro jiné procesy. Proto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klientů musí být důvěryhodný systému a musí být spuštěna s zvláštní oprávnění.  
  
 Aby byl důvěryhodný ke komunikaci s aplikací, které běží na vyšší úrovni oprávnění, musí být podepsané aplikace.  
  
<a name="Manifest_Files"></a>   
## <a name="manifest-files"></a>Soubory manifestu  
 K získání přístupu k systému chráněného [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], aplikace musí být vytvořené s nástroji soubor manifestu, který obsahuje speciální atribut v souboru manifestu. To `uiAccess` atribut je součástí `requestedExecutionLevel` značka, následujícím způsobem:  
  
 `<trustInfo xmlns="urn:0073chemas-microsoft-com:asm.v3">`  
  
 `<security>`  
  
 `<requestedPrivileges>`  
  
 `<requestedExecutionLevel`  
  
 `level="highestAvailable"`  
  
 `UIAccess="true" />`  
  
 `</requestedPrivileges>`  
  
 `</security>`  
  
 `</trustInfo>`  
  
 Hodnota `level` atribut v tento kód je pouze příklad.  
  
 `UIAccess`je "false" ve výchozím nastavení; To znamená, pokud je vynechán atribut, nebo pokud neexistuje žádný manifest pro sestavení, aplikace nebude schopen získat přístup k chráněné [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)].  
  
 Další informace o [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] zabezpečení, podepisování aplikací a na vytváření sestavení manifesty, najdete v části "Vývojáře osvědčené postupy a pokyny pro aplikace v prostředí nejnižšího" na [MSDN](http://msdn.microsoft.com/library/default.asp?url=/library/dnlong/html/AccProtVista.asp).

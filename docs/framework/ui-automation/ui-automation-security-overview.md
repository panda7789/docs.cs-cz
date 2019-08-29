---
title: Přehled zabezpečení automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: 8b798aef528cccdedb1fcaa53c1782632037600d
ms.sourcegitcommit: 77e33b682db39955e331b8e8eda4ef1925a24e78
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2019
ms.locfileid: "70133790"
---
# <a name="ui-automation-security-overview"></a>Přehled zabezpečení automatizace uživatelského rozhraní

> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.

Tento přehled popisuje model zabezpečení pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] v [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)]nástroji.

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a>řízení uživatelských účtů

Zabezpečení je hlavním [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] cílem a mezi inovacemi je schopnost uživatelů spustit jako standardní (bez oprávnění správce), aniž by museli zablokovat spuštěné aplikace a služby, které vyžadují vyšší oprávnění.

V [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]nástroji je většina aplikací dodávána buď s tokenem Standard, nebo s tokenem správce. Pokud aplikaci nelze identifikovat jako aplikaci pro správu, je ve výchozím nastavení spuštěna jako standardní aplikace. Předtím, než bude možné spustit aplikaci určenou jako správce [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] , vyzve uživatele k zadání souhlasu pro spuštění aplikace jako vyšší úrovně. Ve výchozím nastavení se zobrazí výzva k vyjádření souhlasu, a to i v případě, že je uživatel členem místní skupiny Administrators, protože správci spouštějí jako standardní uživatelé, dokud nebude aplikace nebo systémová komponenta vyžadující oprávnění ke spuštění vyžadovat oprávnění správce.

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a>Úlohy vyžadující vyšší oprávnění

Když se uživatel pokusí provést úlohu, která vyžaduje oprávnění správce, zobrazí [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] dialogové okno s výzvou, aby uživatel mohl pokračovat v souhlasu. Toto dialogové okno je chráněno proti komunikaci mezi procesy, takže škodlivý software nemůže simulovat uživatelský vstup. Podobně může být obrazovka pro přihlášení k ploše běžně dostupná pro jiné procesy.

Klienti automatizace uživatelského rozhraní musí komunikovat s jinými procesy, některé z nich možná běží na vyšší úrovni oprávnění. Klienti taky můžou potřebovat přístup k systémovým dialogovým oknům, která nejsou normálně viditelná pro jiné procesy. Proto musí být klienti důvěryhodný systémem a musí běžet se speciálními oprávněními. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]

Aby bylo možné komunikovat s aplikacemi spuštěnými na vyšší úrovni oprávnění, musí být aplikace podepsány.

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a>Soubory manifestu

Chcete-li získat přístup k uživatelskému rozhraní chráněného systému, aplikace musí být sestaveny pomocí souboru `uiAccess` manifestu, který `requestedExecutionLevel` obsahuje atribut ve značce, následovně:

```xml
<trustInfo xmlns="urn:schemas-microsoft-com:asm.v3">
  <security>
    <requestedPrivileges>
      <requestedExecutionLevel
        level="highestAvailable"
        uiAccess="true" />
    </requestedPrivileges>
  </security>
</trustInfo>
```

Hodnota `level` atributu v tomto kódu je pouze příklad.

`uiAccess`má ve výchozím nastavení hodnotu false; To znamená, že pokud je atribut vynechán, nebo pokud neexistuje manifest pro sestavení, aplikace nebude moci získat přístup k chráněnému uživatelskému rozhraní.

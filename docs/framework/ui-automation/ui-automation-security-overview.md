---
title: Přehled zabezpečení automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: 70d24c3dcc531abcec6d4dce75b5f0b31757e0c0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448780"
---
# <a name="ui-automation-security-overview"></a>Přehled zabezpečení automatizace uživatelského rozhraní

> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).

Tento přehled popisuje model zabezpečení pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] v systému Windows Vista.

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a>řízení uživatelských účtů

Zabezpečení je hlavním cílem systému Windows Vista a mezi inovacemi je možnost spouštění uživatelů jako standardní (bez oprávnění správce), aniž by bylo nutné zablokovat spouštění aplikací a služeb, které vyžadují vyšší oprávnění.

V systému Windows Vista je většina aplikací dodávána buď s tokenem Standard, nebo s tokenem správce. Pokud aplikaci nelze identifikovat jako aplikaci pro správu, je ve výchozím nastavení spuštěna jako standardní aplikace. Předtím, než bude možné spustit aplikaci určenou jako správce, systém Windows Vista vyzve uživatele k zadání souhlasu pro spuštění aplikace jako vyšší úrovně. Ve výchozím nastavení se zobrazí výzva k vyjádření souhlasu, a to i v případě, že je uživatel členem místní skupiny Administrators, protože správci spouštějí jako standardní uživatelé, dokud nebude aplikace nebo systémová komponenta vyžadující oprávnění ke spuštění vyžadovat oprávnění správce.

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a>Úlohy vyžadující vyšší oprávnění

Když se uživatel pokusí provést úlohu, která vyžaduje oprávnění správce, systém Windows Vista zobrazí dialogové okno s výzvou, aby bylo možné pokračovat v souhlasu uživatele. Toto dialogové okno je chráněno proti komunikaci mezi procesy, takže škodlivý software nemůže simulovat uživatelský vstup. Podobně může být obrazovka pro přihlášení k ploše běžně dostupná pro jiné procesy.

Klienti automatizace uživatelského rozhraní musí komunikovat s jinými procesy, některé z nich možná běží na vyšší úrovni oprávnění. Klienti taky můžou potřebovat přístup k systémovým dialogovým oknům, která nejsou normálně viditelná pro jiné procesy. Proto [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klienti musí být systémem důvěryhodné a musí běžet se speciálními oprávněními.

Aby bylo možné komunikovat s aplikacemi spuštěnými na vyšší úrovni oprávnění, musí být aplikace podepsány.

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a>Soubory manifestu

Chcete-li získat přístup k uživatelskému rozhraní chráněného systému, musí být aplikace sestaveny pomocí souboru manifestu, který obsahuje atribut `uiAccess` ve značce `requestedExecutionLevel` následujícím způsobem:

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

Hodnota atributu `level` v tomto kódu je pouze příklad.

ve výchozím nastavení má `uiAccess` hodnotu false; To znamená, že pokud je atribut vynechán, nebo pokud neexistuje manifest pro sestavení, aplikace nebude moci získat přístup k chráněnému uživatelskému rozhraní.

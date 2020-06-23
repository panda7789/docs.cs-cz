---
title: Bezpečnostní oprávnění k přesměrování vazby sestavení
description: Přečtěte si o oprávnění zabezpečení vyžadovaného pro explicitní přesměrování vazby sestavení v konfiguračním souboru aplikace v rozhraní .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: a8596bcac4efb0aea07efcfde6726d8bbf148c24
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105088"
---
# <a name="assembly-binding-redirection-security-permission"></a>Bezpečnostní oprávnění k přesměrování vazby sestavení
Explicitní přesměrování vazeb sestavení v konfiguračním souboru aplikace vyžaduje oprávnění zabezpečení. To platí pro přesměrování sestavení rozhraní .NET Framework a sestavení třetích stran. Oprávnění je uděleno nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznaku na <xref:System.Security.Permissions.SecurityPermission> . Spravovaná sestavení nemají ve výchozím nastavení žádná oprávnění.  
  
 Oprávnění zabezpečení je uděleno aplikacím spuštěným v důvěryhodné zóně (místním počítači) a zóně intranetu. Aplikace spuštěné v zóně Internet jsou striktně zakázané při provádění přesměrování vazby sestavení.  
  
 Oprávnění není vyžadováno, pokud je přesměrování sestavení provedeno v souboru zásad vydavatele, který je řízen vydavatelem komponenty, nebo v konfiguračním souboru, který je řízen správcem. Nicméně oprávnění je vyžadováno, aby aplikace explicitně ignorovala zásady vydavatele pomocí [\<publisherPolicy apply="no"/>](./file-schema/runtime/publisherpolicy-element.md) elementu v konfiguračním souboru aplikace.  
  
 Následující tabulka ukazuje výchozí nastavení zabezpečení pro příznak **BindingRedirects** .  
  
|Zóna|Nastavení příznaku BindingRedirects|  
|----------|-----------------------------------|  
|Důvěryhodná zóna (místní počítač)|**PNETE**|  
|Intranetová zóna|**PNETE**|  
|Zóna Internetu|**ZAOKROUHL**|  
|Nedůvěryhodné zóny|**ZAOKROUHL**|  
  
 Správce může změnit tato nastavení zabezpečení na podporu nebo omezení konkrétních scénářů v daném počítači. Neexistují žádné nástroje pro změnu nastavení příznaku **BindingRedirects** z výchozí hodnoty. Správce musí ručně upravit soubor Security.config v počítači uživatele.  
  
## <a name="see-also"></a>Viz také

- [Soubory zásad vydavatele a souběžné spouštění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))
- [Postupy: Povolení a zákaz automatického přesměrování vazby](how-to-enable-and-disable-automatic-binding-redirection.md)
- [Souběžné spouštění](../deployment/side-by-side-execution.md)

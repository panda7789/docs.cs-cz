---
title: Bezpečnostní oprávnění k přesměrování vazby sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: b59689e78f901637674c0a1df28ed74411e8e7c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921377"
---
# <a name="assembly-binding-redirection-security-permission"></a>Bezpečnostní oprávnění k přesměrování vazby sestavení
Explicitní přesměrování vazeb sestavení v konfiguračním souboru aplikace vyžaduje oprávnění zabezpečení. To platí pro přesměrování sestavení rozhraní .NET Framework a sestavení třetích stran. Oprávnění je uděleno nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznaku <xref:System.Security.Permissions.SecurityPermission>na. Spravovaná sestavení nemají ve výchozím nastavení žádná oprávnění.  
  
 Oprávnění zabezpečení je uděleno aplikacím spuštěným v důvěryhodné zóně (místním počítači) a zóně intranetu. Aplikace spuštěné v zóně Internet jsou striktně zakázané při provádění přesměrování vazby sestavení.  
  
 Oprávnění není vyžadováno, pokud je přesměrování sestavení provedeno v souboru zásad vydavatele, který je řízen vydavatelem komponenty, nebo v konfiguračním souboru, který je řízen správcem. Nicméně oprávnění je vyžadováno, aby aplikace explicitně ignorovala zásady vydavatele pomocí [ \<elementu publisherPolicy Apply = "No"/>](./file-schema/runtime/publisherpolicy-element.md) v konfiguračním souboru aplikace.  
  
 Následující tabulka ukazuje výchozí nastavení zabezpečení pro příznak **BindingRedirects** .  
  
|Zóny|Nastavení příznaku BindingRedirects|  
|----------|-----------------------------------|  
|Důvěryhodná zóna (místní počítač)|**PNETE**|  
|Intranet Zone|**PNETE**|  
|Zóna Internetu|**ZAOKROUHL**|  
|Nedůvěryhodné zóny|**ZAOKROUHL**|  
  
 Správce může změnit tato nastavení zabezpečení na podporu nebo omezení konkrétních scénářů v daném počítači. Neexistují žádné nástroje pro změnu nastavení příznaku **BindingRedirects** z výchozí hodnoty. Správce musí ručně upravit soubor Security. config v počítači uživatele.  
  
## <a name="see-also"></a>Viz také:

- [Soubory zásad vydavatele a souběžné spouštění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))
- [Postupy: Povolení a zákaz automatického přesměrování vazby](how-to-enable-and-disable-automatic-binding-redirection.md)
- [Souběžné spouštění](../deployment/side-by-side-execution.md)

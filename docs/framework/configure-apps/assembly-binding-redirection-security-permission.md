---
title: Bezpečnostní oprávnění k přesměrování vazby sestavení
ms.date: 03/30/2017
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
ms.openlocfilehash: ba4e7e790860696f4489e9ef7b73bddcb8c4e399
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61705425"
---
# <a name="assembly-binding-redirection-security-permission"></a>Bezpečnostní oprávnění k přesměrování vazby sestavení
Explicitní přesměrování vazeb sestavení v konfiguračním souboru aplikace vyžaduje oprávnění zabezpečení. To platí pro přesměrování sestavení rozhraní .NET Framework a sestavení třetích stran. Oprávnění je udělován nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznaku <xref:System.Security.Permissions.SecurityPermission>. Spravovaná sestavení nemají žádná oprávnění ve výchozím nastavení.  
  
 Aplikace běžící v zóně důvěryhodných (místní počítač) a zóny intranetu je uděleno oprávnění zabezpečení. Aplikace běžící v zóně Internet výhradně zakázáno provádět přesměrování vazby sestavení.  
  
 Oprávnění není povinný, pokud přesměrování sestavení se provádí v souboru zásad vydavatele, které řídí součásti vydavatele nebo v konfiguračním souboru počítače, které řídí správce. Však oprávnění není vyžadován pro aplikaci explicitně ignorovat pomocí zásady vydavatele [ \<publisherPolicy použít = "žádný" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) prvku v konfiguračním souboru aplikace.  
  
 V následující tabulce jsou uvedeny výchozí nastavení zabezpečení **BindingRedirects** příznak.  
  
|Zóna|Nastavení příznaku BindingRedirects|  
|----------|-----------------------------------|  
|Zóny důvěryhodných serverů (místní počítač)|**ON**|  
|Intranet Zone|**ON**|  
|Zóna Internetu|**OFF**|  
|Nedůvěryhodné zóny|**OFF**|  
  
 Správce může změnit nastavení zabezpečení pro podporu nebo omezit určité scénáře na daný počítač. Nejsou žádné nástroje pro změnu **BindingRedirects** příznak nastavení z výchozí hodnoty; správce musíte ručně upravit soubor Security.config na počítači uživatele.  
  
## <a name="see-also"></a>Viz také:

- [Soubory zásad vydavatele a spuštění vedle sebe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/06d2bae3(v=vs.100))
- [Postupy: Povolení a zákaz automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)
- [Souběžné spouštění](../../../docs/framework/deployment/side-by-side-execution.md)

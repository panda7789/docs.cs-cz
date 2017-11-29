---
title: "Bezpečnostní oprávnění k přesměrování vazby sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- side-by-side execution, assembly binding redirection
- assemblies [.NET Framework], binding redirection
ms.assetid: 24a5cdff-7ed9-4195-93f3-edf6899019fc
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ddaf9965a3b3b5d6171a643b198db93309afad48
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-binding-redirection-security-permission"></a>Bezpečnostní oprávnění k přesměrování vazby sestavení
Explicitní přesměrování vazeb sestavení v konfiguračním souboru aplikace vyžaduje oprávnění zabezpečení. To platí pro přesměrování sestavení rozhraní .NET Framework a sestavení třetích stran. Je povoleno nastavením <xref:System.Security.Permissions.SecurityPermissionFlag> příznak na <xref:System.Security.Permissions.SecurityPermission>. Spravovaná sestavení mít žádná oprávnění ve výchozím nastavení.  
  
 Po udělení oprávnění zabezpečení k aplikacím spuštěným v zóně důvěryhodných (místní počítač) a zóny intranetu. Aplikace běžící v zóně Internet výhradně nesmějí provádění sestavení – přesměrování vazby.  
  
 Pokud sestavení – přesměrování se provádí v souboru zásad vydavatele, které řídí součásti vydavatele nebo v konfiguračním souboru počítače, které řídí správce, není potřeba oprávnění. Je však oprávnění požadovaná pro aplikaci explicitně ignorovat pomocí zásad vydavatele [ \<publisherPolicy použít = "žádný" / >](../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md) element v konfiguračním souboru aplikace.  
  
 Následující tabulka uvádí výchozí nastavení zabezpečení **BindingRedirects** příznak.  
  
|zóny|Nastavení příznaku BindingRedirects|  
|----------|-----------------------------------|  
|Zóny důvěryhodných serverů (místní počítač)|**ON**|  
|Zónu intranetu|**ON**|  
|Zóna Internetu|**VYPNOUT**|  
|Nedůvěryhodné zóny|**VYPNOUT**|  
  
 Správce můžete změnit tato nastavení zabezpečení pro podporu nebo omezit konkrétních scénářů v daném počítači. Neexistují žádné nástroje pro změnu **BindingRedirects** příznak nastavení z výchozího; správce musíte ručně upravit soubor Security.config na počítači uživatele.  
  
## <a name="see-also"></a>Viz také  
 [Vydavatel – soubory zásad a provádění vedle sebe](http://msdn.microsoft.com/en-us/97a042be-4d72-40c3-91c0-76fd36bdf133)  
 [Postupy: povolení a zákaz automatického přesměrování vazby](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)  
 [Spuštění vedle sebe](../../../docs/framework/deployment/side-by-side-execution.md)

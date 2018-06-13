---
title: Fúze globálních statických funkcí
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86cb59c0935c193a9865d5ace5fe11c96226d9e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435900"
---
# <a name="fusion-global-static-functions"></a>Fúze globálních statických funkcí
Tato část popisuje nespravované globální statické funkce, které používá fusion rozhraní API.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ClearDownloadCache – funkce](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 Vymaže globální mezipaměti sestavení stažené sestavení.  
  
 [CompareAssemblyIdentity – funkce](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 Porovná dvě sestavení identity zjistěte, zda jsou ekvivalentní.  
  
 [CreateApplicationContext – funkce](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 Pouze interní. (Tato funkce podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.)  
  
 [CreateAssemblyCache – funkce](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 Získá ukazatel na nový [iassemblycache –](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md) instanci, která představuje globální mezipaměti sestavení.  
  
 [CreateAssemblyEnum – funkce](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 Získá odkazy [iassemblyenum –](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) instance, která reprezentuje seznam objektů, které existují v zadaném sestavení.  
  
 [CreateAssemblyNameObject – funkce](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 Získá odkazy [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) instanci, která představuje jedinečné identity sestavení se zadaným názvem.  
  
 [CreateHistoryReader – funkce](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 Vytvoří historie čtečky zadaný soubor.  
  
 [CreateInstallReferenceEnum – funkce](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 Získá odkazy [iinstallreferenceenum –](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instanci, která představuje seznam odkazů aplikace na zadaném sestavení.  
  
 [GetAppIdAuthority – funkce](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 Získá odkazy [iappidauthority –](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md) instanci, která spravuje klíče pro identity aplikace a odkazy.  
  
 [GetAssemblyIdentityFromFile – funkce](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 Získá odkazy `IUnknown` objekt se zadaným `IID` v sestavení v zadaná cesta k souboru.  
  
 [GetCachePath – funkce](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 Získá cestu k sestavení v mezipaměti, pomocí zadané příznaky.  
  
 [GetHistoryFileDirectory – funkce](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 Načte cestu adresáře historie aplikace.  
  
 [GetIdentityAuthority – funkce](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 Získá odkazy [iidentityauthority –](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md) instanci, která spravuje klíče pro objekty kódu.  
  
 [IsFrameworkAssembly – funkce](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 Získá hodnotu, která určuje, jestli je zadané sestavení spravovaný.  
  
 [NukeDownloadedCache – funkce](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 Odstraní běžné mezipaměti stažení runtime jazyka.  
  
 [PreBindAssemblyEx – funkce](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 Získá po zásady zobrazovaný název sestavení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Rozhraní pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [Výčty pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [Struktury pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [Globální mezipaměť sestavení](../../../../docs/framework/app-domains/gac.md)

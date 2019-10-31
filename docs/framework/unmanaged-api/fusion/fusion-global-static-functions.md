---
title: Fúze globálních statických funkcí
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
ms.openlocfilehash: ff94ed23f3e39888b4f7e255feece99898f8aa74
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108272"
---
# <a name="fusion-global-static-functions"></a>Fúze globálních statických funkcí
Tato část popisuje nespravované globální statické funkce, které používá rozhraní API pro syntézu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ClearDownloadCache – funkce](cleardownloadcache-function.md)  
 Vymaže globální mezipaměť sestavení (GAC) pro stažená sestavení.  
  
 [CompareAssemblyIdentity – funkce](compareassemblyidentity-function.md)  
 Porovná dvě identity sestavení a určí, zda jsou ekvivalentní.  
  
 [CreateApplicationContext – funkce](createapplicationcontext-function.md)  
 Pouze interní. (Tato funkce podporuje infrastrukturu .NET Framework a není určena pro použití přímo v kódu.)  
  
 [CreateAssemblyCache – funkce](createassemblycache-function.md)  
 Získá ukazatel na novou instanci [IAssemblyCache](iassemblycache-interface.md) , která představuje globální mezipaměť sestavení (GAC).  
  
 [CreateAssemblyEnum – funkce](createassemblyenum-function.md)  
 Získá ukazatel na instanci [IAssemblyEnum](iassemblyenum-interface.md) , která představuje seznam objektů, které existují v zadaném sestavení.  
  
 [CreateAssemblyNameObject – funkce](createassemblynameobject-function.md)  
 Získá ukazatel na instanci [IAssemblyName](iassemblyname-interface.md) , která představuje jedinečnou identitu sestavení se zadaným názvem.  
  
 [CreateHistoryReader – funkce](createhistoryreader-function.md)  
 Vytvoří čtečku historie pro zadaný soubor.  
  
 [CreateInstallReferenceEnum – funkce](createinstallreferenceenum-function.md)  
 Získá ukazatel na instanci [IInstallReferenceEnum –](iinstallreferenceenum-interface.md) , která představuje seznam odkazů aplikace na zadané sestavení.  
  
 [GetAppIdAuthority – funkce](getappidauthority-function.md)  
 Získá ukazatel na instanci [IAppIdAuthority –](iappidauthority-interface.md) , která spravuje klíče pro identity aplikace a odkazy.  
  
 [GetAssemblyIdentityFromFile – funkce](getassemblyidentityfromfile-function.md)  
 Získá ukazatel na objekt `IUnknown` se zadaným `IID` v sestavení v zadané cestě k souboru.  
  
 [GetCachePath – funkce](getcachepath-function.md)  
 Načte cestu k sestavení v mezipaměti pomocí zadaných příznaků.  
  
 [GetHistoryFileDirectory – funkce](gethistoryfiledirectory-function.md)  
 Načte cestu k adresáři historie aplikace.  
  
 [GetIdentityAuthority – funkce](getidentityauthority-function.md)  
 Získá ukazatel na instanci [IIdentityAuthority –](iidentityauthority-interface.md) , která spravuje klíče pro objekty kódu.  
  
 [IsFrameworkAssembly – funkce](isframeworkassembly-function.md)  
 Získá hodnotu, která označuje, zda je zadané sestavení spravováno.  
  
 [NukeDownloadedCache – funkce](nukedownloadedcache-function.md)  
 Odstraní mezipaměť pro stažení modulu CLR (Common Language Runtime).  
  
 [PreBindAssemblyEx – funkce](prebindassemblyex-function.md)  
 Načte zobrazovaný název po zásadě pro sestavení.  
  
## <a name="related-sections"></a>Související oddíly  
 [Rozhraní pro fúze](fusion-interfaces.md)  
  
 [Výčty pro fúze](fusion-enumerations.md)  
  
 [Struktury pro fúze](fusion-structures.md)  
  
 [Globální mezipaměť sestavení](../../app-domains/gac.md)

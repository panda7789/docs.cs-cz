---
title: Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 13368dfa7ca9d7981ac146b87e83f77077eaf537
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320727"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a>Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)
Nástroj příkazového řádku konfigurace modelu COM+ (ComSvcConfig. exe) umožňuje konfigurovat rozhraní modelu COM+, která se zveřejňují jako webové služby.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Abyste mohli používat ComSvcConfig. exe, musíte být správce na místním počítači.  
  
 Tento nástroj najdete v následujícím umístění:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation \  
  
 Další informace o nástroji ComSvcConfig. exe najdete v tématu [How to: use com+ service model Configuration Tool](./feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
 Následující tabulka popisuje režimy, které lze použít s ComSvcConfig. exe.  
  
|Možnost|Popis|  
|------------|-----------------|  
|`install`|Nainstaluje konfiguraci pro rozhraní COM+ pro integraci modelu služby.<br /><br /> Krátký tvar `/i`.|  
|`uninstall`|Odinstaluje konfiguraci rozhraní modelu COM+ z integrace modelu služby.<br /><br /> Krátký tvar `/u`.|  
|`list`|Obsahuje seznam informací o aplikacích a součástech modelu COM+, které mají rozhraní konfigurovaná pro integraci Service Model.<br /><br /> Krátký tvar `/l`.|  
  
 Následující tabulka popisuje příznaky, které lze použít s ComSvcConfig. exe.  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/application:` \<*ApplicationId* &#124; *ApplicationName*\>|Určuje aplikaci COM+, která se má nakonfigurovat.<br /><br /> Krátký tvar `/a`.|  
|`/contract:` \< &#124; *identifikátor ProgID* &#124; s ID \*,*InterfaceID* &#124; *Název_rozhraní* &#124; 1 @ no__t-12|Určuje komponentu a rozhraní COM+, které budou nakonfigurovány jako kontrakt pro službu.<br /><br /> Krátký tvar `/c`.<br /><br /> I když se zástupný znak (\*) dá použít při zadání názvu komponenty a rozhraní, doporučujeme, abyste ho nepoužívali, protože můžete vystavovat rozhraní, na která jste se nechtěli zajímat.|  
|`/hosting:` \<*ComPlus* &#124; *byl*\>|Určuje, zda se má použít režim hostování modelu COM+ nebo webový hostující režim.<br /><br /> Krátký tvar `/h`.<br /><br /> Použití hostitelského režimu modelu COM+ vyžaduje explicitní aktivaci aplikace modelu COM+. Použití režimu hostování webu umožňuje, aby se aplikace COM+ automaticky aktivovala podle potřeby. Pokud je aplikace modelu COM+ knihovnou aplikace, běží v procesu Internetová informační služba (IIS). Pokud je aplikace modelu COM+ aplikace serveru, běží v procesu Dllhost. exe.|  
|`/webSite:` \<*website*\>|Určuje web pro hostování při použití režimu hostování webu (viz příznak `/hosting`).<br /><br /> Krátký tvar `/w`.<br /><br /> Pokud není zadán žádný web, použije se výchozí web.|  
|`/webDirectory:` \<*WebDirectory*\>|Určuje virtuální adresář pro hostování při použití webového hostování (viz příznak `/hosting`).<br /><br /> Krátký tvar `/d`.|  
|`/mex`|Přidá koncový bod služby Metadata Exchange (MEX) do výchozí konfigurace služby pro podporu klientů, kteří chtějí načíst definici smlouvy ze služby.<br /><br /> Krátký tvar `/x`.|  
|`/id`|Zobrazí informace o aplikaci, součásti a rozhraní jako ID.<br /><br /> Krátký tvar `/k`.|  
|`/nologo`|Zabraňuje souboru ComSvcConfig. exe zobrazovat jeho logo.<br /><br /> Krátký tvar `/n`.|  
|`/verbose`|Vypíše všechna upozornění nebo informativní text kromě všech zjištěných chyb.<br /><br /> Krátký tvar `/v`.|  
|`/help`|Zobrazí zprávu o využití.<br /><br /> Krátký tvar `/?`.|  
|`/partial`|Vygeneruje konfiguraci služby, když zadané rozhraní obsahuje jeden nebo více podpisů metody, které mohou být vystaveny. V okamžiku inicializace služby se kompatibilní metody zobrazí jako operace v kontraktu služby a nekompatibilní metody jsou ignorovány a chybí od kontraktu služby.<br /><br /> Pokud tento příznak chybí, nástroj nebude generovat konfiguraci služby, když zadané rozhraní obsahuje jednu nebo více nekompatibilních metod.|  
  
## <a name="examples"></a>Příklady  
  
### <a name="description"></a>Popis  
 Následující příklad přidá rozhraní @no__t 0 součásti `ItemOrders.IFinancial` (z aplikace OnlineStore COM+) do sady rozhraní, které jsou vystaveny jako webové služby, a to pomocí hostitelského režimu COM+. Všechna upozornění budou kromě všech zjištěných chyb i výstupy.  
  
### <a name="code"></a>Kód  
  
```console  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>Popis  
 Následující příklad přidá rozhraní @no__t 0 součásti `ItemInventory.Warehouse` (z aplikace OnlineWarehouse COM+) do sady rozhraní, které jsou vystaveny jako webové služby, pomocí režimu hostování webu. Webová služba je hostitelem webu ve virtuálním adresáři OnlineWarehouse služby IIS.  
  
### <a name="code"></a>Kód  
  
```console  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>Popis  
 Následující příklad odebere rozhraní `IFinances` komponenty `ItemOrders.Financial` (z aplikace OnlineStore COM+) ze sady rozhraní, které jsou vystaveny jako webové služby.  
  
### <a name="code"></a>Kód  
  
```console  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a>Popis  
 Následující příklad uvádí seznam aktuálně vydaných hostovaných rozhraní COM+ spolu s odpovídajícími podrobnostmi adres a vazeb pro aplikaci OnlineStore COM+ na místním počítači.  
  
### <a name="code"></a>Kód  
  
```console  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Použití nástroje pro konfiguraci služby modelu COM+](./feature-details/how-to-use-the-com-service-model-configuration-tool.md)

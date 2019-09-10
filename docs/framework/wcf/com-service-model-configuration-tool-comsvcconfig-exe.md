---
title: Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 98c8e50ea4a9efe1c69a0c7b959b228a045dfca1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855655"
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
  
 Další informace o ComSvcConfig. exe naleznete v tématu [How to: Použijte nástroj](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)pro konfiguraci modelu služby com+.  
  
 Následující tabulka popisuje režimy, které lze použít s ComSvcConfig. exe.  
  
|Možnost|Popis|  
|------------|-----------------|  
|`install`|Nainstaluje konfiguraci pro rozhraní COM+ pro integraci modelu služby.<br /><br /> Krátká forma `/i`.|  
|`uninstall`|Odinstaluje konfiguraci rozhraní modelu COM+ z integrace modelu služby.<br /><br /> Krátká forma `/u`.|  
|`list`|Obsahuje seznam informací o aplikacích a součástech modelu COM+, které mají rozhraní konfigurovaná pro integraci Service Model.<br /><br /> Krátká forma `/l`.|  
  
 Následující tabulka popisuje příznaky, které lze použít s ComSvcConfig. exe.  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/application:`&#124; ApplicationId \<ApplicationName\>|Určuje aplikaci COM+, která se má nakonfigurovat.<br /><br /> Krátká forma `/a`.|  
|`/contract:`&#124; &#124; &#124; ClassID ProgID&#124; , InterfaceID Název_rozhraní\* \<    \*\>|Určuje komponentu a rozhraní COM+, které budou nakonfigurovány jako kontrakt pro službu.<br /><br /> Krátká forma `/c`.<br /><br /> I když se zástupný znak\*() dá použít při zadání názvu komponenty a rozhraní, doporučujeme, abyste ho nepoužívali, protože můžete vystavovat rozhraní, které jste nechtěli mít.|  
|`/hosting:`&#124; ComPlus \<byl  \>|Určuje, zda se má použít režim hostování modelu COM+ nebo webový hostující režim.<br /><br /> Krátká forma `/h`.<br /><br /> Použití hostitelského režimu modelu COM+ vyžaduje explicitní aktivaci aplikace modelu COM+. Použití režimu hostování webu umožňuje, aby se aplikace COM+ automaticky aktivovala podle potřeby. Pokud je aplikace modelu COM+ knihovnou aplikace, běží v procesu Internetová informační služba (IIS). Pokud je aplikace modelu COM+ aplikace serveru, běží v procesu Dllhost. exe.|  
|`/webSite:`\< *Webový server*\>|Určuje web pro hostování při použití režimu hostování webu (viz `/hosting` příznak).<br /><br /> Krátká forma `/w`.<br /><br /> Pokud není zadán žádný web, použije se výchozí web.|  
|`/webDirectory:` \<*WebDirectoryName*\>|Určuje virtuální adresář pro hostování při použití webového hostování (viz `/hosting` příznak).<br /><br /> Krátká forma `/d`.|  
|`/mex`|Přidá koncový bod služby Metadata Exchange (MEX) do výchozí konfigurace služby pro podporu klientů, kteří chtějí načíst definici smlouvy ze služby.<br /><br /> Krátká forma `/x`.|  
|`/id`|Zobrazí informace o aplikaci, součásti a rozhraní jako ID.<br /><br /> Krátká forma `/k`.|  
|`/nologo`|Zabraňuje souboru ComSvcConfig. exe zobrazovat jeho logo.<br /><br /> Krátká forma `/n`.|  
|`/verbose`|Vypíše všechna upozornění nebo informativní text kromě všech zjištěných chyb.<br /><br /> Krátká forma `/v`.|  
|`/help`|Zobrazí zprávu o využití.<br /><br /> Krátká forma `/?`.|  
|`/partial`|Vygeneruje konfiguraci služby, když zadané rozhraní obsahuje jeden nebo více podpisů metody, které mohou být vystaveny. V okamžiku inicializace služby se kompatibilní metody zobrazí jako operace v kontraktu služby a nekompatibilní metody jsou ignorovány a chybí od kontraktu služby.<br /><br /> Pokud tento příznak chybí, nástroj nebude generovat konfiguraci služby, když zadané rozhraní obsahuje jednu nebo více nekompatibilních metod.|  
  
## <a name="examples"></a>Příklady  
  
### <a name="description"></a>Popis  
 Následující příklad přidá `IFinances` rozhraní `ItemOrders.IFinancial` komponenty (z aplikace OnlineStore com+) do sady rozhraní, které jsou zpřístupněny jako webové služby, pomocí hostitelského režimu com+. Všechna upozornění budou kromě všech zjištěných chyb i výstupy.  
  
### <a name="code"></a>Kód  
  
```console  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>Popis  
 Následující příklad přidá `IStockLevels` rozhraní `ItemInventory.Warehouse` komponenty (z aplikace OnlineWarehouse com+) do sady rozhraní, které jsou zpřístupněny jako webové služby, pomocí režimu hostování webu. Webová služba je hostitelem webu ve virtuálním adresáři OnlineWarehouse služby IIS.  
  
### <a name="code"></a>Kód  
  
```console  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>Popis  
 Následující příklad odebere `IFinances` rozhraní `ItemOrders.Financial` součásti (z aplikace OnlineStore com+) ze sady rozhraní, které jsou zpřístupněny jako webové služby.  
  
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

- [Postupy: Použití nástroje pro konfiguraci modelu služby COM+](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)

---
title: Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 6d0967355e64640e0fd5c81f04a5bf4f33c7b3f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158655"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a>Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)
Nástroj příkazového řádku modelu COM + Service Model Configuration (ComSvcConfig.exe) můžete nakonfigurovat rozhraní COM +. Chcete-li být vystavena jako webové služby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Musíte být správce na místním počítači použít ComSvcConfig.exe.  
  
 Nástroj najdete v následujícím umístění  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
 Další informace o ComSvcConfig.exe najdete v tématu [jak: Použijte nástroj pro konfiguraci modelu služby COM +](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
 Následující tabulka popisuje režimy, které lze použít s ComSvcConfig.exe.  
  
|Možnost|Popis|  
|------------|-----------------|  
|`install`|Nainstaluje konfigurační rozhraní modelu COM + pro integraci Service Model.<br /><br /> Krátký tvar `/i`.|  
|`uninstall`|Odinstaluje z integrace Service Model configuration pro rozhraní modelu COM +.<br /><br /> Krátký tvar `/u`.|  
|`list`|Obsahuje informace o modelu COM + aplikace a komponenty, které mají rozhraní, které jsou nakonfigurované pro integraci Service Model.<br /><br /> Krátký tvar `/l`.|  
  
 Následující tabulka popisuje příznaky, které lze použít s ComSvcConfig.exe.  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/application:` \<*ApplicationID* &#124; *ApplicationName*\>|Určuje aplikaci COM +. ke konfiguraci.<br /><br /> Krátký tvar `/a`.|  
|`/contract:` \<*ID třídy* &#124; *ProgID* &#124; \*,*InterfaceID* &#124; *InterfaceName*    &#124; \*\>|Určuje komponenty modelu COM + a rozhraní, které budou nakonfigurované jako kontrakt služby.<br /><br /> Krátký tvar `/c`.<br /><br /> Zatímco zástupný znak (\*) lze použít při zadávání názvů součásti a rozhraní, doporučujeme vám, že je velmi riskantní používat, protože může vystavit rozhraní, které jste neměli v úmyslu.|  
|`/hosting:` \<*ComPlus* &#124; *byl*\>|Určuje, zda určený hostující režim nebo režim hostování webu modelu COM +.<br /><br /> Krátký tvar `/h`.<br /><br /> Používání modelu COM + hostující režim vyžaduje explicitní aktivace aplikace modelu COM +. Použití webového hostingu režim umožňuje aplikace modelu COM + automaticky aktivaci jako povinné. Pokud je aplikace modelu COM + aplikace knihovny, běží v procesu Internetové informační služby (IIS). Pokud aplikace modelu COM + je serverová aplikace, spustí se v procesu Dllhost.exe.|  
|`/webSite:` \<*Název webu*\>|Určuje, se používá na webu pro hostování při hostování režimu webu (najdete v článku `/hosting` příznak).<br /><br /> Krátký tvar `/w`.<br /><br /> Pokud není zadán žádný web, použije se výchozí webový server.|  
|`/webDirectory:` \<*WebDirectoryName*\>|Určuje virtuální adresář pro hostování při hostování webu se používá (viz `/hosting` příznak).<br /><br /> Krátký tvar `/d`.|  
|`/mex`|Přidá do výchozí konfigurace služby pro podporu klientů, které chcete načíst definici kontraktu služby koncového bodu služby Metadata Exchange (MEX).<br /><br /> Krátký tvar `/x`.|  
|`/id`|Zobrazí aplikace, komponenty a informace o rozhraní jako identifikátory.<br /><br /> Krátký tvar `/k`.|  
|`/nologo`|Zabrání zobrazení loga. jeho ComSvcConfig.exe.<br /><br /> Krátký tvar `/n`.|  
|`/verbose`|Vypíše všechna upozornění nebo informační text kromě jakékoli došlo k chybám.<br /><br /> Krátký tvar `/v`.|  
|`/help`|Zobrazí zprávu o použití.<br /><br /> Krátký tvar `/?`.|  
|`/partial`|Konfigurace služby generuje, pokud zadané rozhraní obsahuje jeden nebo více podpisy metod, které mohou být zveřejněny. Během inicializace služby kompatibilní metody se zobrazí jako operace v kontraktu služby, a metody není kompatibilní se ignorují a chybí kontrakt služby.<br /><br /> Pokud tento příznak chybí, nástroj se nevygeneruje konfigurace služby při zadané rozhraní obsahuje jednu nebo více nekompatibilních metod.|  
  
## <a name="examples"></a>Příklady  
  
### <a name="description"></a>Popis  
 Následující příklad přidá `IFinances` rozhraní `ItemOrders.IFinancial` komponenty (z OnlineStore aplikace COM +) do sady rozhraní, které jsou vystaveny jako webové služby pomocí hostující režim modelu COM +. Všechna upozornění vydá kromě jakékoli došlo k chybám.  
  
### <a name="code"></a>Kód  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>Popis  
 Následující příklad přidá `IStockLevels` rozhraní `ItemInventory.Warehouse` komponenty (z OnlineWarehouse aplikace COM +) do sady rozhraní, které jsou vystaveny jako webové služby pomocí webového hostující režim. Webová služba je že web hostovaný ve virtuálním adresáři OnlineWarehouse služby IIS.  
  
### <a name="code"></a>Kód  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>Popis  
 Následující příklad odebere `IFinances` rozhraní `ItemOrders.Financial` součásti (z OnlineStore aplikace COM +) ze sady rozhraní, které jsou vystaveny jako webové služby.  
  
### <a name="code"></a>Kód  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a>Popis  
 Následující příklad zobrazí aktuálně vystavit rozhraní modelu COM + hostované, spolu s příslušnou adresou a podrobnosti o vazbu pro aplikaci OnlineStore modelu COM + v místním počítači.  
  
### <a name="code"></a>Kód  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Použijte nástroj pro konfiguraci modelu služby COM +](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)

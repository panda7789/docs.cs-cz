---
title: "Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3f812beea611633fe1fa47ced5db46c462443f28
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a>Nástroj COM+ Service Model Configuration (ComSvcConfig.exe)
Nástroj příkazového řádku modelu COM + Service Model Configuration (ComSvcConfig.exe) umožňuje nakonfigurovat rozhraní modelu COM + mají být exponovány jako webové služby.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Musíte být správce v místním počítači používat ComSvcConfig.exe.  
  
 Tento nástroj naleznete v následujícím umístění  
  
 Foundation\ %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows komunikace  
  
 Další informace o ComSvcConfig.exe najdete v tématu [postupy: použití modelu COM + Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md).  
  
 Následující tabulka popisuje režimy, které lze použít s ComSvcConfig.exe.  
  
|Možnost|Popis|  
|------------|-----------------|  
|`install`|Nainstaluje konfigurační rozhraní modelu COM + modelu služby integrace.<br /><br /> Krátký tvar `/i`.|  
|`uninstall`|Konfigurace pro rozhraní modelu COM + odinstaluje z modelu služby integrace.<br /><br /> Krátký tvar `/u`.|  
|`list`|Zobrazí informace o modelu COM + aplikací a součástí, které mají rozhraní, které jsou nakonfigurované pro integraci Model služby.<br /><br /> Krátký tvar `/l`.|  
  
 Následující tabulka popisuje příznaky, které lze použít s ComSvcConfig.exe.  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/application:`\< *ApplicationID* &#124; *ApplicationName*\>|Určuje aplikace modelu COM + ke konfiguraci.<br /><br /> Krátký tvar `/a`.|  
|`/contract:`\< *Atribut ClassID* &#124; *ProgID* &#124; \*,*ID rozhraní* &#124; *InterfaceName* &#124;\*\>|Určuje komponenty modelu COM + a rozhraní, které budou nakonfigurované jako kontrakt služby.<br /><br /> Krátký tvar `/c`.<br /><br /> Při zástupného znaku (\*) lze použít při zadávání názvů součásti a rozhraní, doporučujeme, abyste že nepoužijete, protože mohou být vystaveny rozhraní, které jste nechtěli.|  
|`/hosting:`\< *complus* &#124; *byl*\>|Určuje, jestli se má používat hostování režim nebo režim hostování webových modelu COM +.<br /><br /> Krátký tvar `/h`.<br /><br /> Použití modelu COM + hostování režim vyžaduje explicitní aktivace aplikace modelu COM +. Použití webového hostingu režim umožňuje aplikace modelu COM + chcete automaticky aktivovat jako vyžaduje. Pokud aplikace modelu COM + je knihovna aplikace, spustí se v procesu Internetové informační služby (IIS). Pokud aplikace modelu COM + je serverová aplikace, spustí se proces Dllhost.exe.|  
|`/webSite:`\< *Název webu*\>|Určuje, se používá na webu při hostování webových hostitelských režimu (v tématu `/hosting` příznak).<br /><br /> Krátký tvar `/w`.<br /><br /> Pokud není zadán žádný web, se používá výchozí webový server.|  
|`/webDirectory:`\< *WebDirectoryName*\>|Určuje virtuální adresář, který pro hostování při publikování na webu se používá (viz `/hosting` příznak).<br /><br /> Krátký tvar `/d`.|  
|`/mex`|Přidá do výchozí konfiguraci služby pro podporu klientů, které chcete získat definici kontraktu ze služby Exchange Metadata (MEX) koncového bodu služby.<br /><br /> Krátký tvar `/x`.|  
|`/id`|Zobrazí aplikace, součásti a informace o rozhraní jako identifikátory.<br /><br /> Krátký tvar `/k`.|  
|`/nologo`|Zabrání zobrazení jeho logo ComSvcConfig.exe.<br /><br /> Krátký tvar `/n`.|  
|`/verbose`|Výstupy všechna upozornění nebo informační text kromě chybám došlo.<br /><br /> Krátký tvar `/v`.|  
|`/help`|Zobrazí zprávu využití.<br /><br /> Krátký tvar `/?`.|  
|`/partial`|Konfigurace služby generuje, pokud zadaný rozhraní obsahuje jeden nebo více metoda podpisy, které mohou být zveřejněny. Během inicializace služby kompatibilní metody zobrazují jako operací na kontrakt služby, a nekompatibilní metody jsou ignorovány a chybí z kontrakt služby.<br /><br /> Pokud chybí tento příznak, nevygeneruje nástroj Konfigurace služby při zadané rozhraní obsahuje jednu nebo více metod nekompatibilní.|  
  
## <a name="examples"></a>Příklady  
  
### <a name="description"></a>Popis  
 Následující příklad přidá `IFinances` rozhraní `ItemOrders.IFinancial` součást (z OnlineStore aplikace COM +) do sady rozhraní, které jsou zveřejněné jako webové služby, pomocí režimu hostování modelu COM +. Všechna upozornění bude výstup kromě chybám došlo.  
  
### <a name="code"></a>Kód  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>Popis  
 Následující příklad přidá `IStockLevels` rozhraní `ItemInventory.Warehouse` součást (z OnlineWarehouse aplikace COM +) do sady rozhraní, které jsou zveřejněné jako webové služby pomocí webového hostingu režimu. Webová služba je že web hostovaný ve virtuálním adresáři OnlineWarehouse služby IIS.  
  
### <a name="code"></a>Kód  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>Popis  
 Následující příklad odebere `IFinances` rozhraní `ItemOrders.Financial` součást (z OnlineStore aplikace COM +) ze sady rozhraní, které jsou zveřejněné jako webové služby.  
  
### <a name="code"></a>Kód  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a>Popis  
 Následující příklad zobrazí aktuálně zveřejňují rozhraní modelu COM + hostované, spolu s odpovídající adresu a podrobnosti o vazby pro aplikaci OnlineStore modelu COM + v místním počítači.  
  
### <a name="code"></a>Kód  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: použití modelu COM + Service Model Configuration Tool](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)

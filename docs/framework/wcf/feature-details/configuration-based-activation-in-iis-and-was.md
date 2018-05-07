---
title: Aktivace založená na konfiguraci v IIS a WAS
ms.date: 03/30/2017
ms.assetid: 6a927e1f-b905-4ee5-ad0f-78265da38238
ms.openlocfilehash: aa4a3c682ab1d5d7ca0869fee588934b9ed2bf75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="configuration-based-activation-in-iis-and-was"></a>Aktivace založená na konfiguraci v IIS a WAS
Za normálních okolností při hostování služby Windows Communication Foundation (WCF) v rámci Internetové informační služby (IIS) nebo služby Aktivace procesů systému Windows (WAS), je nutné zadat soubor .svc. Soubor .svc obsahuje název služby a objekt pro vytváření hostitele volitelné vlastní službu. Tento další soubor přidá režijní náklady na možnosti správy. Aktivace podle konfigurace funkce eliminuje požadavek na soubor .svc a proto přidružené režijní náklady.  
  
## <a name="configuration-based-activation"></a>Aktivace podle konfigurace  
 Aktivace podle konfigurace trvá metadata, která umožňuje umístit do souboru .svc a umístí jej do souboru Web.config. V rámci <`serviceHostingEnvironment`> elementu je <`serviceActivations`> elementu. V rámci <`serviceActivations`> element jsou jeden nebo více <`add`> elementy, jeden pro každou hostovanou službu. <`add`> Element obsahuje atributy, které umožňují nastavit relativní adresu pro službu a typ služby nebo vytváření hostitele služby. Následující příklad kódu konfigurace ukazuje, jak se používá v této části.  
  
> [!NOTE]
>  Každý <`add`> element musí specifikovat, služby nebo atributu objektu pro vytváření. Zadání služby a objektu pro vytváření atributy je povoleno.  
  
```xml  
<serviceHostingEnvironment>  
  <serviceActivations>  
    <add relativeAddress="MyServiceAddress" service="Service" factory="MyServiceHostFactory"/>  
  </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
 Pomocí této v souboru Web.config můžete umístit zdrojový kód služby v adresáři App_Code dodržela sestavení v adresáři Bin aplikace nebo aplikace.  
  
> [!NOTE]
>  -   Při použití aktivace podle konfigurace, vloženého kódu v souborů .svc není podporována.  
> -   `relativeAddress` Musí být nastaven na relativní adresu jako "\<podadresář > / service.svc" nebo "~ /\<directory dílčí, service.svc".  
> -   Když si zaregistrujete relativní adresu, která nemá známou příponou spojené s použitím technologie WCF, je vyvolána výjimka konfigurace.  
> -   Zadaná relativní adresa je relativní vůči kořenovému adresáři virtuální aplikace.  
> -   Kvůli model hierarchické konfigurace jsou registrované relativní adresy na počítači a lokalitou úrovni zděděny virtuální aplikace.  
> -   Registrace v konfiguračním souboru mají přednost před nastavením v .svc .xamlx, XOML nebo jiný soubor.  
> -   Všechny ' \' (zpětná lomítka) v identifikátoru URI odeslaných do služby IIS / se budou automaticky převedeny na / (lomítko). Pokud relativní adresa se přidá, obsahuje ' \' a odeslat identifikátor URI, který používá relativní adresu služby IIS, zpětné lomítko je převeden na dopředné lomítko a služby IIS nesmí shodovat s relativní adresu. Služba IIS odesílá informace trasování, která označuje, že jsou nebyly nalezeny žádné shody.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection.ServiceActivations%2A>  
 [Služby hostování](../../../../docs/framework/wcf/hosting-services.md)  
 [Přehled hostování služeb pracovních postupů](../../../../docs/framework/wcf/feature-details/hosting-workflow-services-overview.md)  
 [\<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)

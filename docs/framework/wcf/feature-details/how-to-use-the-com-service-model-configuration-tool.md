---
title: "Postupy: Použití nástroje pro konfiguraci modelu služby COM+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd89a3333ab68b7d580c813a4b7741686b46c5b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a>Postupy: Použití nástroje pro konfiguraci modelu služby COM+
Jakmile vyberete příslušné hostující režim pomocí nástroje příkazového řádku modelu COM + Service Model Configuration (ComSvcConfig.exe) ke konfiguraci rozhraní aplikace, které se zveřejní jako webové služby.  
  
> [!NOTE]
>  Musíte být správce na počítači lze provádět následující úlohy.  
  
 Při použití ComSvcConfig.exe na počítače s Windows 7 konfigurovat webovou službu, která používá nejnovější verze modelu (aktuálně v4.5), proveďte následující kroky:  
  
1.  Nastavte klíč registru `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` na hodnotu DWORD 0x00000001  
  
2.  Spustit comsvcconfig.exe  
  
3.  Vrátit přidali v kroku 1 zpět na původní hodnotu klíče registru nebo ho odstranit, pokud neexistuje.  
  
> [!IMPORTANT]
>  Při vrácení tohoto klíče registru je důležité. Jedná se o klíč kompatibility. Tato změna není vrácení může způsobit problémy s jinými aplikacemi .NET spuštěná na tomto počítači).  
  
> [!WARNING]
>  Při použití ComSvcConfig.exe/install na počítače s Windows 8, zobrazí se dialogové okno se zobrazí s oznámením "aplikace ve vašem počítači potřebuje následující funkce systému Windows: rozhraní .NET Framework 3.5 (zahrnuje rozhraní .NET 2.0 a .NET 3.0" Pokud není nainstalované rozhraní .NET Framework 3.5. Tento dialog můžete ignorovat. Případně můžete menšit OnlyUseLatestCLR klíče registru na hodnotu DWORD 0x00000001  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>Chcete-li přidat rozhraní do sady rozhraní, která se mají být exponovány jako webové služby, který je hostitelem režimu modelu COM +  
  
-   Spustí ComSvcConfig / pomocí `/install` a `/hosting:complus` možnosti, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     Příkaz přidá `IFinances` rozhraní `ItemOrders.IFinancial` součást (z OnlineStore aplikace COM +) do sady rozhraní, které jsou k dispozici jako webové služby. Služba používá hostování režimu modelu COM + a proto vyžaduje aktivaci explicitní aplikace.  
  
     Pokud pro komponentu a rozhraní můžete použít zástupný znak hvězdičky (*), nepoužívejte ji vzhledem k tomu, že chcete vystavit pouze vybrané funkce jako webovou službu. Po spuštění s budoucí verze této součásti, pomocí zástupného může neúmyslně vystavit rozhraní, která nemusí být při syntaxe konfigurace byla určena.  
  
     / Verbose – možnost instruuje nástroj, který zobrazí upozornění kromě případné chyby.  
  
     Kontrakt služby zveřejněné bude obsahovat všechny metody z `IFinances` rozhraní.  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>Chcete-li přidat pouze konkrétní metody z rozhraní sadu rozhraní, která se mají být exponovány jako webové služby, který je hostitelem režimu modelu COM +  
  
-   Spustí ComSvcConfig / pomocí `/install` a `/hosting:complus` možnosti explicitní názvy požadované metody, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     Příkaz přidá jenom `Credit` a `Debit` metody z `IFinances` rozhraní jako operace zveřejněné servisní smlouvou. Všechny ostatní metody na rozhraní bude vynechán ze smlouvy a nebude možné volat z klienty webové služby.  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a>Přidat sadu rozhraní, která se mají být exponovány jako webové služby, pomocí režimu hostování webových rozhraní  
  
-   Spustí ComSvcConfig / pomocí `/install` možnost a `/hosting:was` možnost, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     Příkaz přidá `IStockLevels` rozhraní na `ItemInventory.Warehouse` součást (z OnlineWarehouse aplikace COM +) do sady rozhraní, které jsou k dispozici jako webové služby. Služba je hostovaná v OnlineWarehouse virtuálního adresáře služby IIS, ne v modelu COM + na webu, a proto bude aplikace automaticky aktivována podle potřeby.  
  
     K použití v rámci procesu konfigurace hostované webové aplikace modelu COM + musí být nakonfigurována pro spuštění jako knihovny aplikace a nikoli serverová aplikace pomocí konzoly pro správu služby komponent. Aplikace, nakonfigurované jako Server aplikace použijte standardní režim hostované webové a způsobit procesu směrování pro každou žádost zpracovat.  
  
     `/mex` Možnost přidá další koncový bod služby Exchange Metadata (MEX), který používá stejné přenosu jako koncový bod služby aplikace pro podporu klientů, které chcete získat definici kontraktu ze služby.  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a>Chcete-li odebrat webové služby pro dané rozhraní  
  
-   Spustí ComSvcConfig / pomocí `/uninstall` možnost, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     Příkaz odebere `IFinances` rozhraní na `ItemOrders.Financial` součásti (z OnlineStore aplikace COM +).  
  
### <a name="to-list-currently-exposed-interfaces"></a>Seznam aktuálně vystavovaných rozhraní  
  
-   Spustí ComSvcConfig / pomocí `/list` možnost, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     Příkaz seznam aktuálně zveřejněné rozhraní, spolu s odpovídající adresu a podrobnosti vazby obor v místním počítači.  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a>Seznam aktuálně konkrétní zveřejněné rozhraní  
  
-   Spustí ComSvcConfig / pomocí `/list` možnost, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     Příkaz seznamy aktuálně zveřejněné modelu COM +-hostované rozhraní, spolu s odpovídající adresu a podrobnosti o vazby pro aplikaci OnlineStore modelu COM + v místním počítači.  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a>Chcete-li zobrazit nápovědu pro možnosti, které lze použít s nástroj  
  
-   Spustí ComSvcConfig / pomocí /? možnost, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Přehled integrace s aplikacemi modelu COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)

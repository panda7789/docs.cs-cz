---
title: 'Postupy: Použití nástroje pro konfiguraci modelu služby COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 67bacade0435f1c63bc79b3282f6bded55b67304
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991588"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a>Postupy: Použití nástroje pro konfiguraci modelu služby COM+
Po výběru vhodného hostitelského režimu použijte nástroj příkazového řádku konfigurace modelu COM+ (ComSvcConfig. exe) ke konfiguraci rozhraní aplikace, která budou vystavena jako webové služby.  
  
> [!NOTE]
> Abyste mohli provádět některé z následujících úkolů, musíte být správcem počítače.  
  
 Při použití nástroje ComSvcConfig. exe na počítači se systémem Windows 7 ke konfiguraci webové služby pro použití nejnovější verze modelu služby (aktuálně v 4.5) proveďte následující kroky:  
  
1. Nastavte klíč `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` registru na hodnotu DWORD 0x00000001.  
  
2. Spusťte ComSvcConfig. exe.  
  
3. Vrátí klíč registru přidaný v kroku 1 zpátky do původní hodnoty nebo ho odstraňte, pokud neexistuje.  
  
> [!IMPORTANT]
> Vrácení tohoto klíče registru je důležité. Toto je klíč kompatibility. Nevrácení této změny může způsobit problémy s jinými aplikacemi .NET běžícími v počítači.  
  
> [!WARNING]
> Při použití ComSvcConfig. exe/install v počítači s Windows 8 se zobrazí dialogové okno s informacemi o tom, že aplikace na vašem počítači potřebuje tuto funkci Windows: .NET Framework 3,5 (zahrnuje .NET 2,0 a .NET 3,0, pokud není nainstalovaná .NET Framework 3,5. Toto dialogové okno může být ignorováno. Alternativně můžete klíč registru OnlyUseLatestCLR SED na hodnotu DWORD 0x00000001.  
  
## <a name="to-add-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-com-hosting-mode"></a>Přidání rozhraní do sady rozhraní vystavených jako webové služby pomocí hostitelského režimu COM+  
  
- Spusťte ComSvcConfig pomocí `/install` možností a `/hosting:complus` , jak je znázorněno v následujícím příkladu.  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     Příkaz přidá `IFinances` rozhraní `ItemOrders.IFinancial` komponenty (z aplikace OnlineStore com+) do sady rozhraní, které budou zveřejněny jako webové služby. Služba používá hostitelský režim modelu COM+, takže vyžaduje explicitní aktivaci aplikace.  
  
     I když znak hvězdičky\*() se dá použít pro komponentu a rozhraní, nepoužívejte ho, protože možná budete chtít vystavit jenom vybrané funkce jako webovou službu. Pokud se spustí s budoucí verzí této součásti, může použití zástupného znaku neúmyslně vystavit rozhraní, které nemusí být k dispozici při určení syntaxe konfigurace.  
  
     Možnost/verbose dá nástroji pokyn, aby zobrazoval upozornění spolu s případnými chybami.  
  
     Kontrakt pro vydanou službu bude obsahovat všechny metody z `IFinances` rozhraní.  
  
## <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-com-hosting-mode"></a>Chcete-li přidat pouze konkrétní metody z rozhraní do sady rozhraní vystavených jako webové služby, pomocí hostitelského režimu COM+  
  
- Spusťte ComSvcConfig pomocí `/install` možností a `/hosting:complus` s explicitním pojmenování požadovaných metod, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     Příkaz přidá pouze `Credit` metody a `Debit` z `IFinances` rozhraní jako operace do vystavené kontraktu služby. Všechny ostatní metody rozhraní budou z kontraktu vynechány a nebude možné je volat od klientů webové služby.  
  
## <a name="to-add-an-interface-to-the-set-of-interfaces-exposed-as-web-services-using-the-web-hosting-mode"></a>Přidání rozhraní do sady rozhraní vystavených jako webové služby pomocí režimu hostování webu  
  
- Spusťte ComSvcConfig pomocí `/install` možnosti `/hosting:was` a možnosti, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     Příkaz přidá `IStockLevels` rozhraní `ItemInventory.Warehouse` součásti (z aplikace OnlineWarehouse com+) do sady rozhraní, které budou zveřejněny jako webové služby. Služba je web hostovaný ve virtuálním adresáři OnlineWarehouse služby IIS, nikoli v modelu COM+, a proto je aplikace automaticky aktivována podle potřeby.  
  
     Chcete-li použít konfiguraci v rámci procesu hostovaného v rámci webu, musí být aplikace modelu COM+ nakonfigurována tak, aby běžela jako aplikace knihovny, nikoli serverová aplikace pomocí konzoly pro správu služby Component Services. Aplikace nakonfigurované jako serverové aplikace používají standardní režim v rámci webu a při zpracování jednotlivých požadavků naúčtují směrování procesu.  
  
     Tato `/mex` možnost přidá koncový bod služby pro výměnu metadat (MEX), který používá stejný přenos jako koncový bod služby aplikace, aby podporoval klienty, kteří chtějí z této služby načíst definici smlouvy.  
  
## <a name="to-remove-a-web-service-for-a-specified-interface"></a>Odebrání webové služby pro zadané rozhraní  
  
- Spusťte ComSvcConfig pomocí `/uninstall` možnosti, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     Příkaz odebere `IFinances` rozhraní `ItemOrders.Financial` součásti (z aplikace modelu COM+ OnlineStore).  
  
## <a name="to-list-currently-exposed-interfaces"></a>Výpis aktuálně vystavených rozhraní  
  
- Spusťte ComSvcConfig pomocí `/list` možnosti, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    ComSvcConfig.exe /list  
    ```  
  
     Příkaz vypíše aktuálně vystavená rozhraní spolu s odpovídajícími podrobnostmi adres a vazeb v oboru pro místní počítač.  
  
## <a name="to-list-specific-currently-exposed-interfaces"></a>Seznam konkrétních aktuálně vystavených rozhraní  
  
- Spusťte ComSvcConfig pomocí `/list` možnosti, jak je znázorněno v následujícím příkladu.  
  
    ```console  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     Příkaz vypíše aktuálně vystavená rozhraní založená na modelu COM+ spolu s odpovídajícími podrobnostmi adres a vazeb pro aplikaci OnlineStore COM+ na místním počítači.  
  
## <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a>Zobrazení pomocníka s možnostmi, které lze použít s nástrojem  
  
- Spustit ComSvcConfig pomocí/? , jak je znázorněno v následujícím příkladu.  
  
    ```console  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Přehled integrace s aplikacemi modelu COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)

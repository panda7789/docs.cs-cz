---
title: 'Postupy: Použití nástroje pro konfiguraci modelu služby COM+'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], using service model configuration tool
ms.assetid: 7e68cd8d-5fda-4641-b92f-290db874376e
ms.openlocfilehash: 5b330a727c0a4a20de13f43fd2844d0b745e5060
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322586"
---
# <a name="how-to-use-the-com-service-model-configuration-tool"></a>Postupy: Použití nástroje pro konfiguraci modelu služby COM+
Jakmile vyberete příslušné hostující režim, použijte nástroj příkazového řádku konfiguraci modelu služby COM + (ComSvcConfig.exe) ke konfiguraci rozhraní aplikací, které se zveřejní jako webové služby.  
  
> [!NOTE]
>  Musíte být správcem na počítači lze provádět následující úlohy.  
  
 Při použití ComSvcConfig.exe konfigurovat webovou službu, která používá nejnovější verze modelu služby (aktuálně v4.5) na počítači s Windows 7, proveďte následující kroky:  
  
1. Nastavte klíč registru `[HKEY_LOCAL_COMPUTER\SOFTWARE\Microsoft\.NETFramework]\OnlyUseLatestCLR` na hodnotu DWORD 0x00000001  
  
2. Spustit comsvcconfig.exe  
  
3. Vrátit přidali v kroku 1 zpět na původní hodnotu klíče registru nebo odstranit, pokud neexistuje.  
  
> [!IMPORTANT]
>  Při vrácení tohoto klíče registru je důležité. Toto je kompatibility klíče. Není při vrácení této změny může způsobit problémy s jinými aplikacemi .NET na počítači spuštěná).  
  
> [!WARNING]
>  Při použití ComSvcConfig.exe/install na počítači s Windows 8 dialogové okno se zobrazí s oznámením "aplikace ve vašem počítači potřebuje následující funkce Windows: rozhraní .NET Framework 3.5 (zahrnuje .NET 2.0 a .NET 3.0" Pokud není nainstalované rozhraní .NET Framework 3.5. Toto dialogové okno může být ignorován. Případně můžete sed OnlyUseLatestCLR klíče registru na hodnotu DWORD 0x00000001  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>Chcete-li přidat rozhraní do sady rozhraní, které mají být vystavena jako webové služby, pomocí hostující režim modelu COM +  
  
-   Spuštění pomocí ComSvcConfig / `/install` a `/hosting:complus` možnosti, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
    ```  
  
     Přidá příkaz `IFinances` rozhraní `ItemOrders.IFinancial` komponenty (z OnlineStore aplikace COM +) do sady rozhraní, která bude vystavena jako webové služby. Služba používá hostující režim modelu COM + a proto vyžaduje aktivaci explicitní aplikace.  
  
     Zástupný znak hvězdička (*) můžete využít pro komponentu a rozhraní, vyhněte se ho používat, protože můžete chtít pouze vybranou funkci jako webovou službu. Spuštění v budoucí verzi této součásti, pomocí zástupného znaku může nechtěně vystavit rozhraní, která nemusí být k dispozici, pokud bylo zjištěno syntaxe konfigurace.  
  
     / Verbose – možnost instruuje nástroj, který zobrazí upozornění kromě nějaké chyby.  
  
     Kontrakt služby vystavené bude obsahovat všechny metody z `IFinances` rozhraní.  
  
### <a name="to-add-only-specific-methods-from-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-com-hosting-mode"></a>Můžete přidat pouze konkrétní metody z rozhraní do sady rozhraní, které mají být vystavena jako webové služby, pomocí hostující režim modelu COM +  
  
-   Spuštění pomocí ComSvcConfig / `/install` a `/hosting:complus` možnosti s explicitní názvy z požadovaných metod, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{Credit,Debit} /hosting:complus /verbose  
    ```  
  
     Tento příkaz přidá pouze `Credit` a `Debit` metody ze `IFinances` rozhraní jako operace pro kontrakt vystavené služby. Všechny metody v rozhraní budou vypuštěny ze smlouvy a nebudou volány z klienty webové služby.  
  
### <a name="to-add-an-interface-to-the-set-of-interfaces-that-are-to-be-exposed-as-web-services-using-the-web-hosting-mode"></a>Chcete-li přidat rozhraní do sady rozhraní, které mají být vystavena jako webové služby, pomocí hostující režim webu  
  
-   Spuštění pomocí ComSvcConfig / `/install` možnost a `/hosting:was` možnosti, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse /mex /verbose  
    ```  
  
     Přidá příkaz `IStockLevels` rozhraní na `ItemInventory.Warehouse` komponenty (z OnlineWarehouse aplikace COM +) do sady rozhraní, která bude vystavena jako webové služby. Služba je hostovaná v OnlineWarehouse virtuální adresář služby IIS, nikoli v modelu COM + na webu, a proto se automaticky aktivuje aplikace podle potřeby.  
  
     K použití v procesu konfigurace hostované webové aplikace modelu COM + nastavené ke spuštění jako knihovny aplikace spíše než serverové aplikace pomocí konzoly pro správu služby Component Services. Aplikace, konfigurované jako Server aplikace použít standardní režim hostované webové a proces směrování pro zpracování každého požadavku se vám účtovat.  
  
     `/mex` Možnost přidá další koncový bod služby Metadata Exchange (MEX), který používá stejné přenosové jako koncový bod služby vaší aplikace pro podporu klientů, které chcete načíst definici kontraktu služby.  
  
### <a name="to-remove-a-web-service-for-a-specified-interface"></a>Chcete-li odebrat webovou službu pro zadané rozhraní  
  
-   Spuštění pomocí ComSvcConfig / `/uninstall` možnosti, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /uninstall /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus  
    ```  
  
     Příkaz odebere `IFinances` rozhraní na `ItemOrders.Financial` (z OnlineStore aplikace COM +).  
  
### <a name="to-list-currently-exposed-interfaces"></a>Na seznamu aktuálně vystavit rozhraní  
  
-   Spuštění pomocí ComSvcConfig / `/list` možnosti, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /list  
    ```  
  
     Příkaz vypíše aktuálně vystavené rozhraní spolu s příslušnou adresou a podrobnosti o vazbu, omezená na místním počítači.  
  
### <a name="to-list-specific-currently-exposed-interfaces"></a>Seznam aktuálně konkrétní vystavit rozhraní  
  
-   Spuštění pomocí ComSvcConfig / `/list` možnosti, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
    ```  
  
     Seznamy příkazů aktuálně vystavena COM +.-hostované rozhraní spolu s příslušnou adresou a podrobnosti o vazbu pro aplikaci OnlineStore modelu COM + v místním počítači.  
  
### <a name="to-display-help-on-the-options-that-can-be-used-with-the-utility"></a>Chcete-li zobrazit nápovědu pro možnosti, které je možné pomocí nástroje  
  
-   Spuštění pomocí ComSvcConfig / /? možnost, jak je znázorněno v následujícím příkladu.  
  
    ```  
    ComSvcConfig.exe /?  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Přehled integrace s aplikacemi modelu COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)

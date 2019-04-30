---
title: Přístupu ke službě z webového prohlížeče (WCF Data Services – rychlý start)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: ebeda2805f3393b298e43aa4dcc601298ce176f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793468"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>Přístupu ke službě z webového prohlížeče (WCF Data Services – rychlý start)

Toto je v druhé úloze tohoto rychlého startu služby WCF Data Services. Při plnění tohoto úkolu spuštění služeb WCF Data Services ze sady Visual Studio a volitelně můžete zakázat čtení informačního kanálu ve webovém prohlížeči. Můžete pak načíst definice dokumentu služby také přístup k prostředkům datové služby, odešlete požadavky HTTP GET přes webový prohlížeč na ohrožené prostředky.

> [!NOTE]
> Ve výchozím nastavení, Visual Studio automaticky přiřadí číslo portu, `localhost` identifikátor URI ve vašem počítači. Tato úloha používá číslo portu `12345` v příkladech identifikátoru URI. Další informace o tom, jak nastavit konkrétní číslo portu v projektu sady Visual Studio naleznete v tématu [vytvoření datové služby](../../../../docs/framework/data/wcf/creating-the-data-service.md).

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>Požádat o výchozí dokument služby pomocí Internet Exploreru

1. V aplikaci Internet Explorer z **nástroje** nabídce vyberte možnost **Možnosti Internetu**, klikněte na tlačítko **obsahu** klikněte na tlačítko **nastavení**a zrušte zaškrtnutí  **Zapnout informačního kanálu zobrazení**.

     Tím zajistíte, který informační kanál čtení je zakázaný. Pokud tato funkce není zakázána, pak webový prohlížeč bude považovat za vrácené AtomPub kódovaného dokumentu XML informačního kanálu místo zobrazují se nezpracovaná data XML.

    > [!NOTE]
    > Pokud váš prohlížeč nelze zobrazit jako nezpracovaná data XML informačního kanálu, by měl stále možné zobrazit jako zdrojový kód pro stránku informačního kanálu.

2. V sadě Visual Studio, stiskněte **F5** spusťte ladění aplikace.

3. Otevřete webový prohlížeč v místním počítači. Na panelu Adresa zadejte následující identifikátor URI:

    ```
    http://localhost:12345/northwind.svc
    ```

     Vrátí výchozí dokument služby, který obsahuje seznam sad entit, které jsou vystaveny touto službou data.

## <a name="to-access-entity-set-resources-from-a-web-browser"></a>Pro přístup k entitě nastavit prostředky z webového prohlížeče

1. Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     Vrátí sadu všem zákazníkům v ukázkové databázi Northwind.

2. Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     Vrátí instanci entity pro konkrétního zákazníka `ALFKI`.

3. Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     To prochází přes vztah mezi zákazníky a objednávkami vrátit sadu všech objednávek pro konkrétního zákazníka `ALFKI`.

4. Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     Tím se vyfiltrují objednávky, které patří do konkrétního zákazníka `ALFKI` tak, aby se vrátí pouze konkrétní pořadí na základě na zadané `OrderID` hodnotu.

## <a name="next-steps"></a>Další kroky

Služby WCF Data Services mají úspěšně přistupovat z webového prohlížeče a prohlížeč vydávající požadavky HTTP GET pro zadané prostředky. Webový prohlížeč poskytuje snadný způsob, jak experimentovat s adresování syntaxe požadavky a prohlédněte si výsledky. Ale za touto metodou obvykle nepřistupuje produkční datové služby. Obvykle aplikace interakci se službou data prostřednictvím aplikace kódu nebo skriptovací jazyky. V dalším kroku vytvoříte klientskou aplikaci, která používá klientské knihovny pro přístup k prostředkům datové služby, jako by byly common language runtime (CLR) objekty:

> [!div class="nextstepaction"]
> [Vytvoření klientské aplikace .NET Framework](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Viz také:

- [Přístup k prostředkům datové služby](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)

---
title: Přístup ke službě z webového prohlížeče (rychlý Start WCF Data Services)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: d89f84cd3ea4f56bbae34cbefe0c3891df96fa8b
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894332"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>Přístup ke službě z webového prohlížeče (rychlý Start WCF Data Services)

Toto je druhý úkol rychlého startu WCF Data Services. V této úloze spustíte WCF Data Services ze sady Visual Studio a případně zakážete čtení informačního kanálu ve webovém prohlížeči. Pak načtete dokument definice služby a také prostředky datové služby přístupu odesláním požadavků HTTP GET prostřednictvím webového prohlížeče na vystavené prostředky.

> [!NOTE]
> Ve výchozím nastavení Visual Studio automaticky přiřadí číslo `localhost` portu identifikátoru URI ve vašem počítači. Tato úloha používá číslo `12345` portu v příkladech identifikátoru URI. Další informace o tom, jak nastavit konkrétní číslo portu v projektu sady Visual Studio, najdete v tématu [Vytvoření datové služby](creating-the-data-service.md).

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>Vyžádání výchozího dokumentu služby pomocí aplikace Internet Explorer

1. V aplikaci Internet Explorer v nabídce **nástroje** vyberte **Možnosti Internetu**, klikněte na kartu **obsah** , klikněte na nastavení a zrušte zaškrtnutí **Možnosti** **zapnout zobrazování informačního kanálu**.

     Tím se zajistí, že čtení informačního kanálu je zakázané. Pokud tuto funkci nezakážete, webový prohlížeč bude s vráceným dokumentem AtomPub zacházet jako s datovým kanálem XML namísto zobrazení nezpracovaných dat XML.

    > [!NOTE]
    > Pokud Váš prohlížeč nemůže informační kanál zobrazit jako nezpracovaná data XML, je vhodné zobrazit informační kanál jako zdrojový kód stránky.

2. V aplikaci Visual Studio stiskněte klávesu **F5** a spusťte ladění aplikace.

3. Otevřete webový prohlížeč na místním počítači. Do adresního řádku zadejte následující identifikátor URI:

    ```http
    http://localhost:12345/northwind.svc
    ```

     Tím se vrátí výchozí dokument služby, který obsahuje seznam sad entit, které jsou zpřístupněny touto datovou službou.

## <a name="to-access-entity-set-resources-from-a-web-browser"></a>Přístup k prostředkům sady entit z webového prohlížeče

1. Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:

    ```http
    http://localhost:12345/northwind.svc/Customers
    ```

     Tím se vrátí sada všech zákazníků v ukázkové databázi Northwind.

2. Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     Tím se vrátí instance entity pro konkrétního zákazníka, `ALFKI`.

3. Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     Tím se projde vztah mezi zákazníky a objednávkami a vrátí sadu všech objednávek pro konkrétního zákazníka `ALFKI`.

4. Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:

    ```http
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     Tato klauzule filtruje objednávky náležející konkrétnímu zákazníkovi `ALFKI` , takže se na základě zadané `OrderID` hodnoty vrátí jenom konkrétní objednávka.

## <a name="next-steps"></a>Další kroky

Úspěšně jste se přistupovali k WCF Data Services z webového prohlížeče, a to v prohlížeči, který vydává požadavky HTTP GET na zadané prostředky. Webový prohlížeč poskytuje snadný způsob, jak experimentovat se syntaxí adresování požadavků a zobrazením výsledků. Tato metoda ale obecně nepoužívá službu produkčních dat. Aplikace obvykle komunikují s datovou službou prostřednictvím kódu aplikace nebo skriptovacích jazyků. V dalším kroku vytvoříte klientskou aplikaci, která používá klientské knihovny pro přístup k prostředkům datové služby, jako by šlo o objekty modulu CLR (Common Language Runtime):

> [!div class="nextstepaction"]
> [Vytvoření klientské aplikace .NET Framework](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a>Viz také:

- [Přístup k prostředkům datové služby](accessing-data-service-resources-wcf-data-services.md)

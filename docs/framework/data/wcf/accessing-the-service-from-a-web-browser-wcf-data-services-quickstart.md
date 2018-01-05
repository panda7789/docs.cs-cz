---
title: "Přístupu ke službě z webového prohlížeče (rychlý start WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71beb254bf258da97207f14afca73cd68c6927ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a>Přístupu ke službě z webového prohlížeče (rychlý start WCF Data Services)
V této úloze se spustí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] z [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] a volitelně zakázat kanál čtení ve webovém prohlížeči. Můžete se pak načtení dokumentu definice služby a také přístup k prostředkům služby data odesláním požadavky HTTP GET prostřednictvím webového prohlížeče na zveřejněné prostředky.  
  
> [!NOTE]
>  Ve výchozím nastavení [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] auto přiřadí číslo portu, `localhost` URI ve vašem počítači. Tato úloha používá číslo portu `12345` v příkladech identifikátor URI. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]jak nastavit konkrétní číslo portu vaše [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] projektu najdete [vytváření službu Data](../../../../docs/framework/data/wcf/creating-the-data-service.md).  
  
### <a name="to-request-the-default-service-document-by-using-internet-explorer"></a>Požádat o výchozí dokument služby v aplikaci Internet Explorer  
  
1.  V aplikaci Internet Explorer z **nástroje** nabídce vyberte možnost **Možnosti Internetu**, klikněte na tlačítko **obsahu** , klikněte na **nastavení**a zrušte zaškrtnutí  **Zapnout informačního kanálu zobrazení**.  
  
     Tím je zajištěno, který informační kanál čtení je zakázána. Pokud tuto funkci nezakážete, pak webový prohlížeč bude považovat za vrácený AtomPub kódovaného dokumentu XML kanálu místo nezpracovaná data XML.  
  
    > [!NOTE]
    >  Pokud váš prohlížeč nemůže zobrazit informační kanál jako nezpracovaná data XML, měli stále mohli zobrazit informační kanál jako zdrojový kód pro stránku.  
  
2.  V [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], stisknutím klávesy F5 spusťte ladění aplikace.  
  
3.  Otevřete webový prohlížeč v místním počítači. Na panelu Adresa zadejte identifikátor URI následující:  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     Vrátí výchozí dokument služby, který obsahuje seznam sad entit zpřístupněných tuto službu data.  
  
### <a name="to-access-entity-set-resources-from-a-web-browser"></a>Pro přístup k entity nastavit prostředky z webového prohlížeče  
  
1.  Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers  
    ```  
  
     Vrátí sadu odběratelů v ukázková databáze Northwind.  
  
2.  Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')  
    ```  
  
     Vrátí instanci entity pro konkrétního zákazníka `ALFKI`.  
  
3.  Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders  
    ```  
  
     To prochází vztah mezi zákazníci a objednávky vrátit sadu všechny objednávky pro konkrétního zákazníka `ALFKI`.  
  
4.  Do adresního řádku webového prohlížeče zadejte následující identifikátor URI:  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643  
    ```  
  
     Tím se odfiltrují objednávky, které patří do konkrétního zákazníka `ALFKI` tak, aby konkrétní pořadí dochází na základě zadaných `OrderID` hodnotu.  
  
## <a name="next-steps"></a>Další kroky  
 Úspěšně jste získali přístup [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] z webového prohlížeče, pomocí prohlížeče vydání HTTP GET požadavky do zadané prostředky. Webový prohlížeč poskytuje snadný způsob, jak experimentovat s adresování syntaxe požadavků a zobrazit výsledky. Datové služby produkční není však přístup obecně touto metodou. Obvykle aplikace komunikovat se službou data prostřednictvím aplikace kód nebo skriptovací jazyky. V dalším kroku vytvoříte klientská aplikace, která používá klientské knihovny pro přístup k prostředkům služby data, jako kdyby byly běžně používané objekty language runtime (CLR):  
  
 [Vytvoření klientské aplikace .NET Framework](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a>Viz také  
 [Přístup k prostředkům datové služby](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)

---
title: Klientské aplikace střední vrstvy
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: 4cca832266b2eb2ab7b1b4eb1a5fe937525db97d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="middle-tier-client-applications"></a>Klientské aplikace střední vrstvy
Toto téma popisuje různé problémy, které jsou specifické pro střední vrstvy klientské aplikace, které používají Windows Communication Foundation (WCF).  
  
## <a name="increasing-middle-tier-client-performance"></a>Zvýšení výkonu klienta střední vrstvy  
 Ve srovnání s předchozí komunikace technologií, jako jsou webové služby pomocí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], vytvoření klienta WCF instance může být složitější z důvodu bohaté sadě funkcí služby WCF. Například když <xref:System.ServiceModel.ChannelFactory%601> je otevřen objekt ji může vytvořit zabezpečené relaci se službou, procedury, která se prodlouží doba spuštění pro instanci klienta. Obvykle se tyto další funkce funkce nemají vliv klientské aplikace výrazně od klienta WCF přes několik nevolá a poté uzavře.  
  
 Střední vrstvy klientské aplikace, ale můžete rychle vytvořit mnoho objektů klienta WCF a v důsledku toho prostředí vyšší inicializace požadavky. Pro zvýšení výkonu aplikací střední vrstvy při volání služby dvěma způsoby:  
  
-   Objekt klienta WCF do mezipaměti a opakovaně pro následující volání, kde je to možné.  
  
-   Vytvoření <xref:System.ServiceModel.ChannelFactory%601> objektu a poté použít k vytvoření nového klienta WCF objekty kanál pro každé volání objektu.  
  
 Problémy, které je třeba zvážit při použití těchto přístupů patří:  
  
-   Pokud služba je zachování stavu specifické pro klienta pomocí relace, nelze vzhledem k tomu, že stav služby je vázaný na střední vrstvě klientských opakovaně klienta WCF střední vrstvy u vrstvy klienta více žádostí.  
  
-   Pokud služba musí provést ověření na základě jednotlivé klienty, musíte vytvořit nového klienta pro každého příchozího požadavku na střední vrstvy, namísto opakovaného použití klienta WCF střední vrstvy (nebo objekt kanálu klienta WCF), protože pověření klienta střední vrstvy nelze změnit po klienta WCF (nebo <xref:System.ServiceModel.ChannelFactory%601>) byla vytvořena.  
  
-   Kanály a klienty vytvořené kanály jsou bezpečné pro přístup z více vláken, nemusí podporují zápis více než jeden zprávy k drátové síti současně. Při odesílání zprávy velké, zvlášť pokud streamování, je operaci odeslání mohou blokovat čekání na další odeslat k dokončení. To způsobí, že dva druhy problémů: chybějících souběžnosti a možnost zablokování Pokud toku řízení vrátí ke službě opakovaného použití kanálu (to znamená, sdílené klienta zavolá službu, jejichž výsledky cesta kódu v zpětné volání pro sdílené klienta). To platí bez ohledu na typ klienta WCF, které můžete znovu použít.  
  
-   Je nutné zajistit chybný kanály bez ohledu na to, jestli sdílet kanál. Když jsou opakovaně kanály, ale můžete chybující kanál vypnout více než jedno čekající žádosti o nebo odeslat.  
  
 Příklad, osvědčené postupy pro opětovné použití klienta pro víc požadavků, naleznete v části [datové vazby v klientovi ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md).  
  
 Kromě toho můžete zvýšit výkon při spuštění pro tyto klienty, kteří používají typy dat, které jsou serializovatelný pomocí <xref:System.Xml.Serialization.XmlSerializer> generování a kompilace kódu serializace pro tyto typy dat za běhu, což může vést k pomalé spuštění výkonu. [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) lze vylepšit výkon spuštění pro tyto aplikace generování kódu nezbytné serializace z kompilované sestavení pro aplikaci. Další informace najdete v tématu [postupy: zlepšení spuštění čas klientských aplikací WCF pomocí třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Viz také  
 [Přístup ke službám pomocí klienta WCF](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)

---
title: Klientské aplikace střední vrstvy
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: 667cc98f46b131fe91e17f3b1b16af429dc597ee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59174080"
---
# <a name="middle-tier-client-applications"></a>Klientské aplikace střední vrstvy
Toto téma popisuje různé problémy, které jsou specifické pro střední vrstvě klientské aplikace, které používají Windows Communication Foundation (WCF).  
  
## <a name="increasing-middle-tier-client-performance"></a>Zvýšení výkonu klienta střední vrstvy  
 Ve srovnání s předchozím komunikace technologií, jako jsou webové služby pomocí [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], vytvoření instance klienta WCF může být složitější z důvodu bohatou sadu funkcí služby WCF. Například, když <xref:System.ServiceModel.ChannelFactory%601> je otevřen objekt navázat zabezpečenou relaci se službou, procedury, která zvyšuje dobu spuštění pro instanci klienta. Obvykle tyto další funkce funkce nemají vliv na klientské aplikace značně od klienta WCF provede několik volání a potom jej zavře.  
  
 Střední vrstvě klientské aplikace, ale můžete rychle vytvořit velký počet objektů klienta WCF a, v důsledku toho prostředí zvýšenou inicializace požadavky. Existují dva hlavní přístupy ke zvýšení výkonu střední vrstvy aplikace při volání služby:  
  
-   Objekt klienta WCF do mezipaměti a použít pro pozdější volání, kde je to možné.  
  
-   Vytvoření <xref:System.ServiceModel.ChannelFactory%601> objektu a pak použít tento objekt k vytvoření nového klienta WCF objekty kanálu pro každé volání.  
  
 Problémy při použití těchto přístupů patří:  
  
-   Pokud služba je zachování stavu specifické pro klienta pomocí relace, pak nelze znovu použít klienta WCF střední vrstvy s žádosti více klientská vrstva vzhledem k tomu, že stav služby je vázán na jazyku klienta střední vrstvy.  
  
-   Pokud služba musí provést ověření na jednotlivé klienty, musíte vytvořit nového klienta pro každého příchozího požadavku ve střední vrstvě. namísto opakovaného použití klienta WCF střední vrstvy (nebo objekt kanálu klienta WCF), protože pověření klienta střední vrstvy nelze změnit po klienta WCF (nebo <xref:System.ServiceModel.ChannelFactory%601>) byla vytvořena.  
  
-   Kanálů a kanály vytvořené klienty jsou bezpečné pro vlákna, se nemusí podporovat zápis více zpráv souběžně do přenosu. Při odesílání velkých zpráv, zejména v případě, že datový proud, je operace odeslání může blokovat čekání na další odeslat k dokončení. To způsobí, že dva druhy problémů: Nedostatečná souběžnost a možnost zablokování Pokud tok řízení vrátí do služby opětovné použití kanálu (to znamená, sdílené klient zavolá službu cesty kódu, jejichž výsledky ve zpětném volání do sdílené klienta). To platí bez ohledu na typ klienta WCF, který je znovu použít.  
  
-   Je třeba ošetřit chybnou kanály bez ohledu na to, zda sdílet kanál. Když kanály jsou opakovaně používat, ale můžete neškodné kanálu více než jeden žádostí čekajících na vyřízení nebo odeslat.  
  
 Příklad, který ukazuje osvědčené postupy pro opětovné použití klienta více žádostí, najdete v části [datové vazby v klientovi ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md).  
  
 Kromě toho můžete zvýšit výkon při spouštění pro tyto klienty, kteří používají datové typy, které jsou serializovatelné pomocí <xref:System.Xml.Serialization.XmlSerializer> generování a kompilaci kódu serializace pro typy dat za běhu, což může vést k pomalé spouštění výkonu. [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) výkon lze zvýšit objem požadovaný při spuštění pro tyto aplikace generování kódu serializace nezbytné ze zkompilovaných sestavení pro aplikaci. Další informace najdete v tématu [jak: Vylepšení spuštění čas z klientských aplikací WCF pomocí třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Viz také:

- [Přístup ke službám pomocí klienta WCF](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)

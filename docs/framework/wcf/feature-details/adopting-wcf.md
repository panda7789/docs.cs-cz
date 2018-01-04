---
title: "Přijetí WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 522d4d39df6df62a6bed2fdc9f6d72df1193faca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="adopting-windows-communication-foundation"></a>Přijetí WCF
Můžete použít [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pro nový vývoj, když budete pokračovat, chcete-li zachovat stávající aplikace vyvinuté pomocí technologie ASP.NET. Protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je by měla být nejvhodnější volbou pro usnadnění komunikace s aplikace vytvořené pomocí rozhraní .NET Framework v žádném scénáři, mohl sloužit jako standardní nástroj pro širokou škálu problémy s komunikací softwaru způsobem řešení aby nelze ASP.NET.  
  
 Nové [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mohou být aplikace nasazeny na počítačích, stejný jako stávající webových služeb ASP.NET. Pokud existujících webových služeb ASP.NET použijte verzi rozhraní .NET Framework verze 2.0, pak můžete použít nástroj ASP.NET IIS Registration selektivně nasazení rozhraní .NET Framework 2.0 do aplikace služby IIS, ve kterém nové [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace jsou pro hostování. Tento nástroj je popsána v [ASP.NET IIS Registration Tool (Aspnet_regiis.exe)](http://go.microsoft.com/fwlink/?LinkId=94687), a je součástí uživatelské rozhraní konzoly pro správu služby IIS 6.0.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]slouží k přidání nových funkcí do existující webových služeb ASP.NET přidáním [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, které jsou nakonfigurovány na spuštění v režimu kompatibility ASP.NET do stávajících aplikací ASP.NET – webové služby ve službě IIS. Z důvodu režimu kompatibility ASP.NET, kód pro nové [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby můžete používat a aktualizovat stejné informace o stavu aplikace jako existující kódu ASP.NET pomocí <xref:System.Web.HttpContext> třídy. Aplikace můžou taky sdílet stejné knihovny tříd.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Klienti mohou používat webových služeb ASP.NET. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby, které jsou nakonfigurované <xref:System.ServiceModel.BasicHttpBinding> mohou být využívána klienty webové služby ASP.NET. ASP.NET – webové služby může existovat společně s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] lze použít i pro přidání funkcí do existující webové služby ASP.NET. Všechny tyto způsoby zadané ve kterém [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a webových služeb ASP.NET je možné společně použít, můžete chtít migrace webových služeb ASP.NET na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pouze v případě, že budete potřebovat funkce, které jsou poskytovány [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a není webových služeb ASP.NET.  
  
 I v několika případech, kdy je nezbytné pečlivě zvažte, že migrace kód z jednoho technologie do jiného je málokdy správný přístup. Důvodem pro přijetí nové technologie je splňují nové požadavky, které nelze splnit s dřívější technologie a v takovém případě správný krokem je návrhu nové řešení ke splnění nově rozšířit sadu požadavků. Nové výhody návrhu z vašich zkušeností s stávajícího systému a moudrý získávají vzhledem k tomu, že byla navržená tak, že systému. Nový design použít také veškeré funkce nové technologie a ne reprodukci staré návrhu na nové platformě. Po vytváření prototypů klíčové prvky nového návrhu bude jednodušší opětovné použití kódu z existujícího systému v rámci nového.  
  
 V několika případech, kde Portování ze ASP.NET Web služeb na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je správným řešením v následujícím oddílu najdete některé pokyny o tom, jak pokračovat. Není Rady, jak migrovat služby a jak migraci klientů.  
  
 Dokončení analýzy o tom, jak migrovat existující webové služby ASP.NET na WCF najdete v tématu [webových služeb ASP.NET a Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkID=71761). Tato část popisuje, jak implementovat kompatibilní služby WCF z metadat pro vás webovou službu ASP.NET a postup migrace kódu klienta a služby webové technologie ASP.NET do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Načítání metadat a implementace kompatibilní služby](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)  
 [Postupy: Migrace kódu webové služby ASP.NET na Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)  
 [Postupy: Migrace kódu klienta webové služby ASP.NET na Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)

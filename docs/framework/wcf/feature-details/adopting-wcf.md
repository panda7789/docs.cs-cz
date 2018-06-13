---
title: Přijetí WCF
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: bcd6543e6cd47dc723b308acebec6f492fa14fb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489128"
---
# <a name="adopting-windows-communication-foundation"></a>Přijetí WCF
Můžete používat Windows Communication Foundation (WCF) pro nový vývoj nadále zachovat stávající aplikace vyvinuté pomocí technologie ASP.NET. Protože WCF má být nejvhodnější volbou pro usnadnění komunikace s aplikace vytvořené pomocí rozhraní .NET Framework v žádném scénáři, mohl sloužit jako standardní nástroj pro řešení širokou škálu problémy s komunikací softwaru tak, že technologie ASP.NET nelze provést.  
  
 Nové aplikace WCF můžete nasadit na stejný počítače jako existující webové služby ASP.NET. Pokud existujících webových služeb ASP.NET použijte verzi rozhraní .NET Framework verze 2.0, můžete použít ASP.NET IIS Registration Tool selektivně nasazení do aplikace služby IIS, ve kterých jsou nové aplikace WCF pro hostování rozhraní .NET Framework 2.0. Tento nástroj je popsána v [ASP.NET IIS Registration Tool (Aspnet_regiis.exe)](http://go.microsoft.com/fwlink/?LinkId=94687), a je součástí uživatelské rozhraní konzoly pro správu služby IIS 6.0.  
  
 WCF slouží k přidání nových funkcí do existující webových služeb ASP.NET přidáním služby WCF, které jsou nakonfigurovány na spuštění v režimu kompatibility ASP.NET do stávajících aplikací ASP.NET – webové služby ve službě IIS. Z důvodu režimu kompatibility ASP.NET, můžete používat a aktualizovat stejné informace o stavu aplikace jako existující kódu ASP.NET pomocí kód pro nové služby WCF <xref:System.Web.HttpContext> třídy. Aplikace můžou taky sdílet stejné knihovny tříd.  
  
 Klienti WCF pomocí webových služeb ASP.NET. Služby WCF, které jsou nakonfigurovány s <xref:System.ServiceModel.BasicHttpBinding> mohou být využívána klienty webové služby ASP.NET. Webových služeb ASP.NET může existovat společně s aplikací služby WCF a WCF lze použít i pro přidání funkcí do existující webové služby ASP.NET. Zadány všechny tyto způsoby, ve kterých WCF a ASP.NET Web services můžete použít společně, můžete migrovat webových služeb ASP.NET na WCF pouze v případě, že budete potřebovat funkce, které jsou k dispozici službami WCF a není ASP.NET Web.  
  
 I v několika případech, kdy je nezbytné pečlivě zvažte, že migrace kód z jednoho technologie do jiného je málokdy správný přístup. Důvodem pro přijetí nové technologie je splňují nové požadavky, které nelze splnit s dřívější technologie a v takovém případě správný krokem je návrhu nové řešení ke splnění nově rozšířit sadu požadavků. Nové výhody návrhu z vašich zkušeností s stávajícího systému a moudrý získávají vzhledem k tomu, že byla navržená tak, že systému. Nový design použít také veškeré funkce nové technologie a ne reprodukci staré návrhu na nové platformě. Po vytváření prototypů klíčové prvky nového návrhu bude jednodušší opětovné použití kódu z existujícího systému v rámci nového.  
  
 Pro několik případů, kde portování z webových služeb ASP.NET na WCF je správným řešením, v následujícím oddílu najdete některé pokyny o tom, jak pokračovat. Není Rady, jak migrovat služby a jak migraci klientů.  
  
 Dokončení analýzy o tom, jak migrovat existující webové služby ASP.NET na WCF najdete v tématu [webových služeb ASP.NET a Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkID=71761). Tato část popisuje, jak implementovat kompatibilní služby WCF z metadat pro vás webovou službu ASP.NET a jak migrovat ASP.NET Web kód klienta a služby WCF.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Načítání metadat a implementace kompatibilní služby](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)  
 [Postupy: Migrace kódu webové služby ASP.NET na Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)  
 [Postupy: Migrace kódu klienta webové služby ASP.NET na Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-client-to-wcf.md)

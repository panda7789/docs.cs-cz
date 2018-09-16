---
title: Přijetí WCF
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: 5773d2687eb06cfc562dbe25fa9b94864b1b3a49
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45676597"
---
# <a name="adopting-windows-communication-foundation"></a>Přijetí WCF

Můžete použít Windows Communication Foundation (WCF) pro vývoj nových projektů, když budete pokračovat k údržbě stávajících aplikací vyvinutých pomocí technologie ASP.NET. Protože WCF má být nejvhodnější volbou pro usnadnění komunikace s aplikací vytvořených pomocí rozhraní .NET Framework ve všech scénářích, může sloužit jako standardní nástroj pro řešení nejrůznější komunikační problémy se softwarem způsobem, že technologie ASP.NET nelze provést.

Nové aplikace WCF je nasadit na stejných počítačů jako existující webové služby ASP.NET. Pokud existujících webových služeb ASP.NET s používat verzi rozhraní .NET Framework starší než verze 2.0, můžete používat ASP.NET IIS Registration Tool selektivně nasazení do aplikace služby IIS, ve kterých jsou nové aplikace WCF zajistit také jejich hostování rozhraní .NET Framework 2.0. Tento nástroj je popsána v [registrační nástroj služby IIS technologie ASP.NET (Aspnet_regiis.exe)](https://go.microsoft.com/fwlink/?LinkId=94687), a je součástí uživatelského rozhraní konzoly pro správu služby IIS 6.0.

WCF slouží k přidání nových funkcí do existující webové služby ASP.NET tak, že přidáte služby WCF, které jsou nakonfigurovány na spouštění v režimu kompatibility ASP.NET do stávajících aplikací technologie ASP.NET webové služby ve službě IIS. Z důvodu režim kompatibility ASP.NET, můžete používat a aktualizovat stejné informace o stavu aplikace jako již existující kód technologie ASP.NET, pomocí kódu pro nové služby WCF <xref:System.Web.HttpContext> třídy. Aplikace můžou také sdílet stejné knihovny tříd.

Klienti WCF pomocí webové služby ASP.NET. Služby WCF, které mají nakonfigurované <xref:System.ServiceModel.BasicHttpBinding> mohou využívat klienty webové služby ASP.NET. Webové služby ASP.NET může existovat vedle sebe s aplikací služby WCF a WCF slouží i k přidání funkcí do existující webové služby ASP.NET. S ohledem všechny z těchto způsobů, jimiž lze společně použít služby WCF a ASP.NET Web, můžete chtít migrace webových služeb ASP.NET na WCF pouze v případě, že vyžadujete funkce, které jsou k dispozici službami WCF a není v prostředí ASP.NET.

I v několika případech, kdy je nezbytné je migrace kódu z jedné technologie do jiného zřídka správný přístup. Důvod pro přijetí nové technologie je splnit nové požadavky, které nelze splnit dřívějších technologií a v takovém případě je správnou věc udělat pro návrh nové řešení, které vyhoví nově rozšířit sadu požadavků. Nových návrhu výhodách z vašich zkušeností s ve stávajícím systému a při získané od takového systému byla navržena. Nový design můžete také použít všechny funkce nové technologie a ne reprodukce původního návrhu na nové platformě. Po vytváření prototypů klíčové prvky nového návrhu máme snadnější k opakovanému použití kódu z existujících systému v rámci nového.

## <a name="see-also"></a>Viz také

- [Postupy: Načítání metadat a implementace kompatibilní služby](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)

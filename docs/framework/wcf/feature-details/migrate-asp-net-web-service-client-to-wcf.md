---
title: 'Postupy: Migrace kódu klienta webové služby ASP.NET do služby Windows Communication Foundation'
ms.date: 03/30/2017
ms.assetid: 2e0a22a7-e1d5-4718-8997-4319a7cd9027
ms.openlocfilehash: cb60f9cb2e8f35ee703b049eae9e3d99c1ec7d49
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491127"
---
# <a name="how-to-migrate-aspnet-web-service-client-code-to-the-windows-communication-foundation"></a>Postupy: Migrace kódu klienta webové služby ASP.NET do služby Windows Communication Foundation
Následující postup popisuje obecné kroky, které je třeba dodržet do migrace kódu klienta webové služby ASP.NET do WCF.  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-migrate-aspnet-web-service-client-code-to-wcf"></a>Do migrace kódu klienta webové služby ASP.NET do WCF  
  
1.  Ujistěte se, že o komplexní sadu testů pro klienta neexistují.  
  
2.  Pomocí sady Visual Studio 2005 můžete upgradovat klienta aplikace rozhraní .NET 2.0. Spusťte sadu testů.  
  
3.  Odebrání klientského projektu ASP.NET kód klienta. Tento kód se generuje pomocí nástroje WSDL.exe moduly.  
  
4.  Generovat pomocí kódu klienta WCF [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Přidání tohoto kódu do projektu klienta a sloučit výstup konfigurace do klienta existující konfigurační soubor.  
  
5.  Kompilace aplikace. Opravte chyby kompilace nahrazením odkazy na bývalé typů klientů ASP.NET s odkazy na nové typy klienta WCF.  
  
6.  Spusťte sadu testů.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Migrace kódu webové služby ASP.NET na Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/migrate-asp-net-web-service-to-wcf.md)

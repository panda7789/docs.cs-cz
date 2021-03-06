---
title: Klientská knihovna pro WCF Data Services
description: Naučte se používat klientské knihovny WCF Data Services pro přístup k datům z klientské aplikace .NET Framework a jejich změny.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 58d038d5c2ac4973c2b41f4d49c1746f48f2a2fb
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247737"
---
# <a name="wcf-data-services-client-library"></a>Klientská knihovna pro WCF Data Services
Jakákoli aplikace může komunikovat s datovou službou založenou na protokolu OData (Open Data Protocol), pokud může odeslat požadavek HTTP a zpracovat datový kanál OData, který vrátí datová služba. Tato vzájemná funkční spolupráce umožňuje přístup ke službám založeným na standardu OData z široké škály aplikací s podporou webu. WCF Data Services obsahuje klientské knihovny, které poskytují bohatší programovací prostředí při využívání kanálů OData z .NET Framework nebo aplikací založených na programu Silverlight.  
  
 Dvě hlavní třídy klientské knihovny jsou <xref:System.Data.Services.Client.DataServiceContext> třídy a <xref:System.Data.Services.Client.DataServiceQuery%601> třídy. <xref:System.Data.Services.Client.DataServiceContext>Třída zapouzdřuje operace, které jsou podporovány pro zadanou datovou službu. I když služba OData je Bezstavová, kontext není. Proto můžete použít <xref:System.Data.Services.Client.DataServiceContext> třídu k údržbě stavu klienta mezi interakcemi s datovou službou, aby bylo možné podporovat funkce, jako je například Správa změn. Tato třída také spravuje identity a sleduje změny. <xref:System.Data.Services.Client.DataServiceQuery%601>Třída reprezentuje dotaz na konkrétní sadu entit.  
  
 Tato část popisuje, jak používat klientské knihovny pro přístup k datům z klientské aplikace .NET Framework a jejich změně. Další informace o použití klientské knihovny WCF Data Services s aplikací založenou na programu Silverlight naleznete v tématu [WCF Data Services (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v%3dvs.95)). K dispozici jsou další klientské knihovny, které umožňují využívat informační kanál OData v jiných typech aplikací. Další informace o sadě OData SDK naleznete v tématu [sada OData SDK – vzorový kód](https://www.odata.org/ecosystem/#sdk).
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Generování klientské knihovny datové služby](generating-the-data-service-client-library-wcf-data-services.md)  
 Popisuje, jak vygenerovat klientské knihovny a třídy datové služby klienta založené na kanálech OData.  
  
 [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)  
 Popisuje, jak zadat dotaz na datovou službu z aplikace založené na .NET Framework pomocí klientských knihoven.  
  
 [Načtení odloženého obsahu](loading-deferred-content-wcf-data-services.md)  
 V této části najdete popis postupu při načítání dalšího obsahu, který není zahrnutý v počáteční reakci na dotaz.  
  
 [Aktualizace datové služby](updating-the-data-service-wcf-data-services.md)  
 Popisuje, jak vytvářet, upravovat a odstraňovat entity a vztahy pomocí klientských knihoven.  
  
 [Asynchronní operace](asynchronous-operations-wcf-data-services.md)  
 Popisuje zařízení poskytovaná klientskými knihovnami pro práci s datovou službou asynchronním způsobem.  
  
 [Operace dávkování](batching-operations-wcf-data-services.md)  
 V této části najdete popis postupu odesílání více požadavků do datové služby v jedné dávce pomocí klientských knihoven.  
  
 [Vazba dat k ovládacím prvkům](binding-data-to-controls-wcf-data-services.md)  
 Popisuje, jak navazovat ovládací prvky s datovým kanálem OData vráceným datovou službou.  
  
 [Operace volání služeb](calling-service-operations-wcf-data-services.md)  
 Popisuje, jak používat klientskou knihovnu pro volání operací služby.  
  
 [Správa kontextu datové služby](managing-the-data-service-context-wcf-data-services.md)  
 Popisuje možnosti správy chování klientské knihovny.  
  
 [Práce s binárními daty](working-with-binary-data-wcf-data-services.md)  
 Popisuje způsob přístupu a změny binárních dat vrácených datovou službou jako datový proud.  
  
## <a name="see-also"></a>Viz také

- [Definování datových služeb WCF Data Services](defining-wcf-data-services.md)
- [Začínáme](getting-started-with-wcf-data-services.md)

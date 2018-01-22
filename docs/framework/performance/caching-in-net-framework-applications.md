---
title: "Ukládání do vyrovnávací paměti v aplikacích .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ASP.NET caching
- caching [.NET Framework]
- caching [ASP.NET]
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
caps.latest.revision: "26"
author: tdykstra
ms.author: tdykstra
manager: wpickett
ms.workload: tdykstra
ms.openlocfilehash: 9429a1a1eeef82c7587ef573f6413e45a4e97a91
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="caching-in-net-framework-applications"></a>Ukládání do vyrovnávací paměti v aplikacích .NET Framework
Ukládání do mezipaměti umožňuje ukládání dat v paměti pro rychlý přístup. Když je znovu přístupu k datům, aplikací můžete získat data z mezipaměti nutné načíst z původního zdroje. Tím lze vylepšit výkon a škálovatelnost. Navíc díky ukládání dat do mezipaměti k dispozici při zdroj dat je dočasně nedostupný.  
  
 Rozhraní .NET Framework poskytuje ukládání do mezipaměti funkce, které můžete použít ke zlepšení výkonu a škálovatelnosti obou klientských a serverových aplikací pro Windows, včetně ASP.NET.  
  
> [!NOTE]
>  V [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] a starší verze technologie ASP.NET poskytuje implementace v mezipaměti v paměti <xref:System.Web.Caching> oboru názvů. V předchozích verzích [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], ukládání do mezipaměti byla k dispozici pouze v <xref:System.Web> obor názvů a proto vyžaduje závislost na třídy technologie ASP.NET. V rozhraní .NET Framework 4 <xref:System.Runtime.Caching> obor názvů obsahuje rozhraní API, které jsou určené pro Web a jiných webových aplikací.  
  
## <a name="caching-data"></a>Ukládaní dat do mezipaměti  
 Může ukládat pomocí třídy v mezipaměti informace <xref:System.Runtime.Caching> oboru názvů. Ukládání do mezipaměti třídy v tomto oboru názvů zadejte následující funkce:  
  
-   Abstraktní typy, které tvoří základ pro vytvoření vlastní mezipaměti implementace.  
  
-   Implementace mezipaměti konkrétní objekt v paměti.  
  
 Abstraktní základní třída ukládání do mezipaměti (<xref:System.Runtime.Caching.ObjectCache>) definuje následující úlohy ukládání do mezipaměti:  
  
-   Vytváření a Správa položek v mezipaměti.  
  
-   Zadáním informací o vypršení platnosti a jeho vyřazení.  
  
-   Spouštěcí události, které jsou vyvolány v reakci na změny v položky mezipaměti.  
  
 <xref:System.Runtime.Caching.MemoryCache> Třída je implementací mezipaměti v paměti objektu <xref:System.Runtime.Caching.ObjectCache> třídy. Můžete použít <xref:System.Runtime.Caching.MemoryCache> třídu pro většinu úloh ukládání do mezipaměti.  
  
> [!NOTE]
>  <xref:System.Runtime.Caching.MemoryCache> Třída je založena na objekt mezipaměti ASP.NET, která je definována v modelu <xref:System.Web.Caching> oboru názvů. Proto interní ukládání do mezipaměti logiku podobná logiku, která byla poskytnuta v předchozích verzích technologie ASP.NET.  
  
 Příklad, jak používat k ukládání do mezipaměti v aplikaci WPF, naleznete v části [návod: ukládání dat aplikací v aplikaci WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md).  
  
## <a name="caching-in-aspnet-applications"></a>Ukládání do mezipaměti v aplikacích ASP.NET  
 Ukládání do mezipaměti v třídy <xref:System.Runtime.Caching> obor názvů poskytují funkce pro ukládání do mezipaměti data technologie ASP.NET.  
  
> [!NOTE]
>  Pokud aplikace cílena [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] nebo starší, musíte použít ukládání do mezipaměti třídy, které jsou definovány v <xref:System.Web.Caching> oboru názvů. Další informace najdete v tématu [přehled ukládání do mezipaměti technologie ASP.NET](http://msdn.microsoft.com/library/5ec28012-4972-4dc3-b3e8-9d20401fe11d).  
  
> [!NOTE]
>  Při vývoji nových aplikací doporučujeme používat <xref:System.Runtime.Caching.MemoryCache> třídy. Rozhraní API, která je součástí <xref:System.Runtime.Caching> obor názvů je jako rozhraní API, která je součástí <xref:System.Web.Caching.Cache> oboru názvů. Rozhraní API proto bude známé, pokud jste použili ukládání do mezipaměti v předchozích verzích technologie ASP.NET. Příklad použití ukládání do mezipaměti v aplikacích ASP.NET naleznete v části [návod: ukládání dat aplikací technologie ASP.NET](http://msdn.microsoft.com/library/942236f6-0138-4aaf-af71-a5ea451a1e23).  
  
### <a name="output-caching"></a>Ukládání výstupu do mezipaměti  
 Ručně data do mezipaměti aplikace, můžete použít <xref:System.Runtime.Caching.MemoryCache> třídy v prostředí ASP.NET. Technologie ASP.NET také podporuje ukládání výstupu do mezipaměti, která ukládá generovaný výstup stránky, ovládací prvky a odpovědi protokolu HTTP v paměti. Můžete nakonfigurovat ukládání výstupu do mezipaměti deklarativně na webovou stránku ASP.NET nebo pomocí nastavení v souboru Web.config. Další informace najdete v tématu [outputCache Element pro ukládání do mezipaměti (schéma nastavení ASP.NET)](http://msdn.microsoft.com/library/47cd2b47-316f-4dfd-bbf8-539be3066fee).  
  
 Technologie ASP.NET umožňuje rozšířit ukládání výstupu do mezipaměti tak, že vytvoříte vlastní zprostředkovatelé výstupní mezipaměti. Pomocí vlastních poskytovatelů můžete ukládat obsah uložený v mezipaměti pomocí jiných zařízení úložiště například disky, cloudového úložiště a distribuované mezipaměti moduly. Pokud chcete vytvořit poskytovatel vlastní výstupní mezipaměti, můžete vytvořit třídu odvozenou z <xref:System.Web.Caching.OutputCacheProvider> třídy a nakonfigurovat aplikaci, aby používala poskytovatel vlastní výstupní mezipaměti.  
  
## <a name="caching-in-wcf-rest-services"></a>Ukládání do mezipaměti v služby REST WCF  
 Pro služby WCF REST rozhraní .NET Framework umožňuje využít výhod deklarativní ukládání výstupu do mezipaměti, která je k dispozici v technologii ASP.NET. To vám umožní do mezipaměti odpovědi z vaší operací služby WCF REST. Když uživatel odešle požadavek HTTP GET pro službu, která je nakonfigurovaná pro ukládání do mezipaměti, ASP.NET zašle zpět odpověď uložená v mezipaměti a není volána metoda služby. Po vypršení platnosti mezipaměti, při příštím uživatel odešle požadavek HTTP GET vaší služby metoda je volána a odpověď je znovu do mezipaměti.  
  
 Rozhraní .NET Framework také umožňuje implementovat podmíněného HTTP GET ukládání do mezipaměti. Ve scénářích REST podmíněného požadavek HTTP GET se často používá služby k implementaci inteligentního ukládání do mezipaměti protokolu HTTP, jak je popsáno v [specifikace protokolu HTTP](http://go.microsoft.com/fwlink/?LinkId=165800). Další informace najdete v tématu [ukládání do mezipaměti podporu pro webové služby HTTP WCF](http://go.microsoft.com/fwlink/?LinkId=184598).  
  
## <a name="extending-caching-in-the-net-framework"></a>Rozšíření ukládání do mezipaměti v rozhraní .NET Framework  
 Ukládání do mezipaměti v rozhraní .NET Framework je určena pro rozšiřitelnost. <xref:System.Runtime.Caching.ObjectCache> Třída umožňuje vytvářet vlastní mezipaměti implementace. Tato třída poskytuje členů, které jsou k dispozici pro všechny spravované aplikace, včetně Windows Forms, Windows Presentation Foundation (WPF) a Windows Communications Foundation (WCF). Můžete to třeba udělat před vytvořením mezipaměti třídu, která používá mechanismus jiného úložiště nebo pokud chcete, aby podrobnou kontrolu nad operace mezipaměti.  
  
 Ukládání do mezipaměti můžete rozšířit můžete provést následující:  
  
-   Vytvořte vlastní třídu, která je odvozena z <xref:System.Runtime.Caching.ObjectCache> třídy a pak zadejte vlastní mezipaměti implementaci v odvozené třídě.  
  
-   Vytvořte třídu, která je odvozena z <xref:System.Runtime.Caching.MemoryCache> třídy a přizpůsobit nebo rozšířit odvozené třídy. Příklad toho, jak to provést, naleznete v části [ukládání dat aplikací pomocí více mezipaměti objektů v aplikaci ASP.NET](http://blogs.msdn.com/aspnetue/archive/2010/03/22/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application.aspx).  
  
-   Vytvořte třídu, která je odvozena z <xref:System.Web.Caching.OutputCacheProvider> třídy a nakonfigurovat aplikaci, aby používala poskytovatel vlastní výstupní mezipaměti.  
  
 Další informace naleznete v příspěvku [Extensible ukládání výstupu do mezipaměti technologie ASP.NET 4 (VS 2010 a rozhraní .NET 4.0 řady)](http://go.microsoft.com/fwlink/?LinkId=185772) na blogu Scott Guthrie.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching.MemoryCache>  
 [Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)  
 [Návod: Ukládání dat aplikací technologie ASP.NET](http://msdn.microsoft.com/library/942236f6-0138-4aaf-af71-a5ea451a1e23)

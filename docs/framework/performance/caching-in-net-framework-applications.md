---
title: Ukládání do vyrovnávací paměti v aplikacích .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- ASP.NET caching
- caching [.NET Framework]
- caching [ASP.NET]
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
author: tdykstra
ms.openlocfilehash: 4d9451f99b0253d0a4de6550b64fedd7fdfeda77
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862014"
---
# <a name="caching-in-net-framework-applications"></a>Ukládání do vyrovnávací paměti v aplikacích .NET Framework
Ukládání do mezipaměti umožňuje uložit data do paměti pro rychlý přístup. Když je znovu přístupu k datům, aplikacím můžete získat data z mezipaměti namísto načítání z původního zdroje. Tím lze vylepšit výkon a škálovatelnost. Navíc umožňuje ukládání dat do mezipaměti k dispozici při zdroj dat je dočasně nedostupný.  
  
 Rozhraní .NET Framework poskytuje ukládání do mezipaměti funkce, které můžete využít ke zlepšení výkonu a škálovatelnosti i Windows klientských a serverových aplikací, včetně ASP.NET.  
  
> [!NOTE]
>  V [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] a starší verze technologie ASP.NET poskytuje implementaci mezipaměti v paměti v <xref:System.Web.Caching> oboru názvů. V předchozích verzích [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], ukládání do mezipaměti byla k dispozici pouze ve <xref:System.Web> obor názvů a proto požadovaná závislost na třídách technologie ASP.NET. V rozhraní .NET Framework 4 <xref:System.Runtime.Caching> obor názvů obsahuje rozhraní API, která jsou navrženy pro webové a jiných webových aplikací.  
  
## <a name="caching-data"></a>Ukládaní dat do mezipaměti  
 Můžete ukládat do mezipaměti informace pomocí tříd v <xref:System.Runtime.Caching> oboru názvů. Ukládání do mezipaměti třídy v tomto oboru názvů poskytují následující funkce:  
  
-   Abstraktní typy, které poskytují základ pro vytvoření vlastní mezipaměti implementací.  
  
-   Implementace mezipaměti konkrétních objektů v paměti do mezipaměti.  
  
 Abstraktní základní třída ukládání do mezipaměti (<xref:System.Runtime.Caching.ObjectCache>) definuje následující úlohy ukládání do mezipaměti:  
  
-   Vytváření a Správa položek v mezipaměti.  
  
-   Zadání informací o vypršení platnosti a vyřazení.  
  
-   Aktivace události, které jsou vyvolány v reakci na změny položky mezipaměti.  
  
 <xref:System.Runtime.Caching.MemoryCache> Třída je implementace mezipaměti objektů v paměti do mezipaměti <xref:System.Runtime.Caching.ObjectCache> třídy. Můžete použít <xref:System.Runtime.Caching.MemoryCache> třídu pro většinu úkolů s mezipamětí.  
  
> [!NOTE]
>  <xref:System.Runtime.Caching.MemoryCache> Třídy je modelovaná objektu mezipaměti ASP.NET, která je definována v <xref:System.Web.Caching> oboru názvů. Proto interní ukládání do mezipaměti logiku podobnou logiku, která byla k dispozici v předchozích verzích technologie ASP.NET.  
  
 Příklad, jak používat ukládání do mezipaměti v aplikaci WPF, naleznete v tématu [návod: ukládání dat aplikací v aplikaci WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md).  
  
## <a name="caching-in-aspnet-applications"></a>Ukládání do mezipaměti v aplikacích ASP.NET  
 Ukládání do mezipaměti v třídy <xref:System.Runtime.Caching> obor názvů poskytuje funkce pro ukládání dat v ASP.NET do mezipaměti.  
  
> [!NOTE]
>  Pokud vaše aplikace cílí [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] nebo starší, musí používat ukládání do mezipaměti tříd, které jsou definovány v <xref:System.Web.Caching> oboru názvů. Další informace najdete v tématu [přehled ukládání do mezipaměti ASP.NET](https://msdn.microsoft.com/library/5ec28012-4972-4dc3-b3e8-9d20401fe11d).  
  
> [!NOTE]
>  Při vývoji nových aplikací, doporučujeme použít <xref:System.Runtime.Caching.MemoryCache> třídy. Rozhraní API, která je součástí <xref:System.Runtime.Caching> obor názvů je jako rozhraní API, která je součástí <xref:System.Web.Caching.Cache> oboru názvů. Rozhraní API proto bude známé, pokud jste použili v předchozích verzích technologie ASP.NET do mezipaměti. Příklad, jak používat ukládání do mezipaměti v aplikacích ASP.NET, naleznete v tématu [návod: ukládání dat aplikací v ASP.NET](https://msdn.microsoft.com/library/942236f6-0138-4aaf-af71-a5ea451a1e23).  
  
### <a name="output-caching"></a>Ukládání výstupu do mezipaměti  
 Ručně aplikace ukládat data do mezipaměti, můžete použít <xref:System.Runtime.Caching.MemoryCache> třídy v prostředí ASP.NET. Technologie ASP.NET také podporuje ukládání výstupu do mezipaměti, který uloží vygenerovaný výstup stránky, ovládací prvky a odpovědi protokolu HTTP v paměti. Můžete konfigurovat ukládání výstupu do mezipaměti deklarativně v webová stránka ASP.NET nebo pomocí nastavení v souboru Web.config. Další informace najdete v tématu [outputCache – Element pro ukládání do mezipaměti (schéma nastavení technologie ASP.NET)](https://msdn.microsoft.com/library/47cd2b47-316f-4dfd-bbf8-539be3066fee).  
  
 Technologie ASP.NET umožňuje rozšířit ukládání výstupu do mezipaměti tak, že vytvoříte vlastního zprostředkovatele mezipaměti výstupu. S použitím vlastních zprostředkovatelů, můžete ukládat obsah uložený v mezipaměti pomocí jiných zařízení úložišť, jako jsou disky, cloudového úložiště a moduly distribuované mezipaměti. K vytvoření vlastního zprostředkovatele mezipaměti výstupu, vytvořte třídu, která je odvozena z <xref:System.Web.Caching.OutputCacheProvider> třídy a konfigurace aplikace pro použití vlastního zprostředkovatele mezipaměti výstupu.  
  
## <a name="caching-in-wcf-rest-services"></a>Ukládání do mezipaměti ve službách WCF REST  
 Pro služby WCF REST rozhraní .NET Framework vám umožní využít deklarativní výstupu do mezipaměti, která je k dispozici v technologii ASP.NET. To vám umožní do mezipaměti odpovědi z vašich operací služby WCF REST. Když uživatel odešle požadavek HTTP GET na službu, která je nakonfigurovaná pro ukládání do mezipaměti, ASP.NET, odešle zpět odpověď uložená v mezipaměti, a není volána metoda služby. Po vypršení platnosti mezipaměti, při příštím uživatel odešle požadavek HTTP GET, je volána metoda vaše služby a znovu do mezipaměti odpovědi.  
  
 Rozhraní .NET Framework také umožňuje implementovat podmíněný HTTP GET ukládání do mezipaměti. V ostatních případech Podmíněný požadavek HTTP GET často dělají, když služby k implementaci inteligentního ukládání do mezipaměti HTTP, jak je popsáno v [specifikaci protokolu HTTP](https://go.microsoft.com/fwlink/?LinkId=165800). Další informace najdete v tématu [podporu ukládání do mezipaměti pro webové služby HTTP WCF](https://go.microsoft.com/fwlink/?LinkId=184598).  
  
## <a name="extending-caching-in-the-net-framework"></a>Rozšíření ukládání do mezipaměti v rozhraní .NET Framework  
 Ukládání do mezipaměti v rozhraní .NET Framework byla navržena jako rozšiřitelné. <xref:System.Runtime.Caching.ObjectCache> Třída umožňuje vytvoření vlastní mezipaměti implementace. Tato třída obsahuje členy, které jsou k dispozici pro všechny spravované aplikace, včetně Windows Forms a Windows Presentation Foundation (WPF), Windows Communications Foundation (WCF). Můžete takto například chcete-li vytvořit třídu mezipaměti, která používá mechanismus jiného úložiště nebo pokud chcete podrobnou kontrolu nad operace s mezipamětí.  
  
 Rozšířit ukládání do mezipaměti můžete provádět následující akce:  
  
-   Vytvoření vlastní třídy, která je odvozena z <xref:System.Runtime.Caching.ObjectCache> třídy a pak zadejte vlastní mezipaměti implementaci v odvozené třídě.  
  
-   Vytvořte třídu, která je odvozena z <xref:System.Runtime.Caching.MemoryCache> třídy a přizpůsobte si nebo rozšiřte odvozené třídy. Příklad toho, jak to provést, najdete v části [ukládání dat aplikací pomocí více mezipaměti objektů v aplikaci ASP.NET](https://blogs.msdn.com/aspnetue/archive/2010/03/22/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application.aspx).  
  
-   Vytvořte třídu, která je odvozena z <xref:System.Web.Caching.OutputCacheProvider> třídy a konfigurace aplikace pro použití vlastního zprostředkovatele mezipaměti výstupu.  
  
 Další informace naleznete v příspěvku [Extensible ukládání výstupu do mezipaměti ASP.NET 4 (VS 2010 a řady rozhraní .NET 4.0)](https://go.microsoft.com/fwlink/?LinkId=185772) v blogu Scotta Guthrie.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching.MemoryCache>  
 [Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)  
 [Návod: Ukládání dat aplikací v ASP.NET](https://msdn.microsoft.com/library/942236f6-0138-4aaf-af71-a5ea451a1e23)

---
title: Ukládání do vyrovnávací paměti v aplikacích .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- ASP.NET caching
- caching [.NET Framework]
- caching [ASP.NET]
ms.assetid: c4b47ee0-4b82-4124-9bce-818088385e34
ms.openlocfilehash: 779785e9793939cf121fedf99b23a07288173637
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967609"
---
# <a name="caching-in-net-framework-applications"></a>Ukládání do vyrovnávací paměti v aplikacích .NET Framework
Ukládání do mezipaměti umožňuje ukládat data v paměti pro rychlý přístup. Po opětovném přístup k datům mohou aplikace získat data z mezipaměti, nikoli načíst je z původního zdroje. To může zvýšit výkon a škálovatelnost. Ukládání do mezipaměti navíc zpřístupňuje data v případě, že zdroj dat není dočasně k dispozici.  
  
 .NET Framework poskytuje funkce pro ukládání do mezipaměti, které můžete použít ke zlepšení výkonu a škálovatelnosti klientských a serverových aplikací pro Windows, včetně ASP.NET.  
  
> [!NOTE]
> V .NET Framework 3,5 a dřívějších verzích poskytuje ASP.NET implementaci mezipaměti v paměti v <xref:System.Web.Caching> oboru názvů. V předchozích verzích .NET Framework bylo ukládání do mezipaměti k dispozici pouze v <xref:System.Web> oboru názvů, a proto je vyžadována závislost na třídách ASP.NET. V .NET Framework 4 <xref:System.Runtime.Caching> obor názvů obsahuje rozhraní API navržená pro webové i newebové aplikace.  
  
## <a name="caching-data"></a>Ukládaní dat do mezipaměti  
 Informace můžete ukládat do mezipaměti pomocí tříd v <xref:System.Runtime.Caching> oboru názvů. Třídy pro ukládání do mezipaměti v tomto oboru názvů poskytují následující funkce:  
  
- Abstraktní typy, které poskytují základ pro vytváření vlastních implementací mezipaměti.  
  
- Konkrétní implementace mezipaměti objektů v paměti.  
  
 Abstraktní základní třída pro ukládání do<xref:System.Runtime.Caching.ObjectCache>mezipaměti () definuje následující úlohy ukládání do mezipaměti:  
  
- Vytváření a Správa položek mezipaměti.  
  
- Zadání informací o vypršení platnosti a vyřazení.  
  
- Aktivuje události, které jsou vyvolány v reakci na změny v položkách mezipaměti.  
  
 Třída je implementací <xref:System.Runtime.Caching.ObjectCache> mezipaměti objektů v paměti třídy. <xref:System.Runtime.Caching.MemoryCache> <xref:System.Runtime.Caching.MemoryCache> Třídu můžete použít pro většinu úloh ukládání do mezipaměti.  
  
> [!NOTE]
> Třída je modelována v objektu ASP.NET Cache, který je definován <xref:System.Web.Caching> v oboru názvů. <xref:System.Runtime.Caching.MemoryCache> Proto interní logika ukládání do mezipaměti bude podobná logice, která byla poskytnuta v dřívějších verzích ASP.NET.  
  
 Příklad použití pro ukládání do mezipaměti v aplikaci WPF naleznete v tématu [Návod: Ukládání aplikačních dat do mezipaměti v](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)aplikaci WPF.  
  
## <a name="caching-in-aspnet-applications"></a>Ukládání do mezipaměti v aplikacích ASP.NET  
 Třídy ukládání do mezipaměti v <xref:System.Runtime.Caching> oboru názvů poskytují funkce pro ukládání dat do mezipaměti v ASP.NET.  
  
> [!NOTE]
> Pokud je vaše aplikace cílena na .NET Framework 3,5 nebo starší, je nutné použít třídy mezipaměti, které jsou definovány <xref:System.Web.Caching> v oboru názvů. Další informace najdete v tématu [Přehled ukládání do mezipaměti ASP.NET](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).  
  
> [!NOTE]
> Při vývoji nových aplikací doporučujeme použít <xref:System.Runtime.Caching.MemoryCache> třídu. Rozhraní API, které je k dispozici v <xref:System.Runtime.Caching> oboru názvů, je podobné rozhraní API, které je k dispozici <xref:System.Web.Caching.Cache> v oboru názvů. Rozhraní API proto bude známé, pokud jste v dřívějších verzích ASP.NET použili ukládání do mezipaměti. Příklad použití ukládání do mezipaměti v aplikacích ASP.NET naleznete v tématu [Návod: Ukládání dat aplikací do mezipaměti](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100))v ASP.NET.  
  
### <a name="output-caching"></a>Ukládání výstupu do mezipaměti  
 Chcete-li ručně uložit data aplikace do mezipaměti, <xref:System.Runtime.Caching.MemoryCache> můžete použít třídu v ASP.NET. ASP.NET podporuje také ukládání výstupu do mezipaměti, který ukládá generovaný výstup stránek, ovládacích prvků a odpovědí HTTP do paměti. Ukládání výstupu do mezipaměti můžete nakonfigurovat deklarativně na webové stránce ASP.NET nebo pomocí nastavení v souboru Web. config. Další informace naleznete v tématu [element OutputCache pro ukládání do mezipaměti (schéma nastavení ASP.NET)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms228124(v=vs.100)).  
  
 ASP.NET umožňuje rozšiřování výstupu do mezipaměti tím, že vytváří vlastní poskytovatele výstupní mezipaměti. Pomocí vlastních zprostředkovatelů můžete ukládat obsah uložený v mezipaměti pomocí jiných úložných zařízení, jako jsou disky, cloudové úložiště a moduly distribuované mezipaměti. Chcete-li vytvořit vlastního poskytovatele výstupní mezipaměti, vytvořte třídu, která je odvozena z <xref:System.Web.Caching.OutputCacheProvider> třídy, a nakonfigurujte aplikaci tak, aby používala vlastního zprostředkovatele výstupní mezipaměti.  
  
## <a name="caching-in-wcf-rest-services"></a>Ukládání do mezipaměti v WCF REST Services  
 U WCF REST Services umožňuje .NET Framework využít výhod deklarativního ukládání výstupu do mezipaměti, které je k dispozici v ASP.NET. Díky tomu můžete ukládat odpovědi z operací služby WCF REST. Když uživatel odešle požadavek HTTP GET do služby, která je nakonfigurovaná pro ukládání do mezipaměti, ASP.NET odešle zpět odpověď uloženou v mezipaměti a metoda služby se nevolá. Po vypršení platnosti mezipaměti bude při příštím odeslání požadavku HTTP GET vyvolána vaše metoda služby a odpověď se znovu uloží do mezipaměti.  
  
 .NET Framework taky umožňuje implementovat podmíněný mezipaměť HTTP GET. V případě scénářů REST se služba často používá k implementaci inteligentního ukládání do mezipaměti protokolu HTTP, jak je popsáno ve [specifikaci http](https://go.microsoft.com/fwlink/?LinkId=165800). Další informace najdete v tématu [Podpora ukládání do mezipaměti pro webové HTTP služby WCF](https://go.microsoft.com/fwlink/?LinkId=184598).  
  
## <a name="extending-caching-in-the-net-framework"></a>Rozšíření ukládání do mezipaměti v .NET Framework  
 Ukládání do mezipaměti v .NET Framework je navrženo jako rozšiřitelné. <xref:System.Runtime.Caching.ObjectCache> Třída umožňuje vytvořit vlastní implementaci mezipaměti. Tato třída poskytuje členy, kteří jsou k dispozici pro všechny spravované aplikace, včetně model Windows Forms, Windows Presentation Foundation (WPF) a Windows Communications Foundation (WCF). Můžete to udělat tak, aby bylo možné vytvořit třídu mezipaměti, která používá jiný mechanismus úložiště, nebo pokud chcete detailní kontrolu nad operacemi mezipaměti.  
  
 K rozšiřování mezipaměti můžete postupovat takto:  
  
- Vytvořte vlastní třídu, která je odvozena z <xref:System.Runtime.Caching.ObjectCache> třídy a pak Poskytněte vlastní implementaci mezipaměti v odvozené třídě.  
  
- Vytvořte třídu, která je odvozena <xref:System.Runtime.Caching.MemoryCache> z třídy a přizpůsobte nebo rozšiřuje odvozenou třídu. Příklad toho, jak to provést, najdete v tématu [ukládání aplikačních dat do mezipaměti pomocí více objektů mezipaměti v aplikaci ASP.NET](https://blogs.msdn.com/aspnetue/archive/2010/03/22/caching-application-data-by-using-multiple-cache-objects-in-an-asp-net-application.aspx).  
  
- Vytvořte třídu, která je odvozena z <xref:System.Web.Caching.OutputCacheProvider> třídy a nakonfigurujte aplikaci tak, aby používala vlastního zprostředkovatele výstupní mezipaměti.  
  
 Další informace najdete v tématu rozšiřitelné [ukládání výstupu do mezipaměti s ASP.NET 4 (VS 2010 a .net 4,0 Series)](https://go.microsoft.com/fwlink/?LinkId=185772) na blogu Scott Guthrie.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching.MemoryCache>
- [Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF](../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
- [Návod: Ukládání aplikačních dat do mezipaměti v ASP.NET](https://docs.microsoft.com/previous-versions/ff477235(v=vs.100))

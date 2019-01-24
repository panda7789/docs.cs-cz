---
title: 'Úložiště Thread Local: Statická pole relativní vůči vláknu a datové sloty ve vztahu'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69107cd7f1f84fa402479bb8a76c4b9b8a825d69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718257"
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>Úložiště Thread Local: Statická pole relativní vůči vláknu a datové sloty ve vztahu
Můžete použít spravovaného úložiště thread local (TLS) k ukládání dat, který je jedinečný k doméně vlákna a aplikace. Rozhraní .NET Framework poskytuje dva způsoby, jak používat spravované TLS: statická pole a datové sloty relativní vůči vláknu.  
  
-   Použít statická pole relativní vůči vláknu (relativní vůči vláknu `Shared` pole v jazyce Visual Basic) Pokud očekáváte vaše konkrétní požadavky v době kompilace. Statická pole relativní vůči vláknu poskytovat nejlepší výkon. Také poskytují výhody kontrola typu v době kompilace.  
  
-   Používejte datové sloty ve vztahu skutečné požadavky může být zjištěny pouze v době běhu. Datové sloty ve vztahu jsou pomalejší a větší než statická pole relativní vůči vláknu není vhodný, a data se ukládají jako typ <xref:System.Object>, takže musíte vysílat na správný typ před jejich použitím.  
  
 V nespravované C++ pomocí `TlsAlloc` dynamicky přidělit slotů a `__declspec(thread)` deklarovat, že by měla být proměnná přidělená v úložišti relativní vůči vláknu. Statická pole a datové sloty relativní vůči vláknu poskytují spravovaná verze tohoto chování.  
  
 V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> třídy za účelem vytvoření místních objektů, které jsou inicializována pomalu, když je objekt nejprve zpracován. Další informace najdete v tématu [opožděné inicializace](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Jedinečnost dat ve spravované TLS  
 Ať už používáte statická pole relativní vůči vláknu nebo datové sloty ve vztahu, data ve spravované TLS jsou jedinečné pro kombinaci domény vlákna a aplikace.  
  
-   V doméně aplikace nelze jedno vlákno upravovat data z jiného vlákna, i když oba vlákna použít stejné pole nebo slotu.  
  
-   Při vlákno přistupuje ke stejné pole nebo slotu z několika domén aplikace, samostatné hodnota se zachová v každé doméně aplikace.  
  
 Například pokud vlákna nastaví hodnotu statická pole relativní vůči vláknu, přejde do jiné doméně aplikace a pak načte hodnotu pole, hodnota získali v druhém doménu aplikace se liší od hodnoty v první domény aplikace. Nastavení nové hodnoty pro pole ve druhém doménu aplikace nemá vliv na hodnotu pole v prvním aplikační doméně.  
  
 Podobně když vlákno získá stejný slot s názvem dat ve dvou různých aplikačních doménách, data v první doména aplikace zůstane nezávisle na data v druhém doménu aplikace.  
  
## <a name="thread-relative-static-fields"></a>Statická pole relativní vůči vláknu  
 Pokud víte, že část dat je vždy jedinečné pro kombinaci domény aplikace a vlákna, použije <xref:System.ThreadStaticAttribute> atribut pro statické pole. Pole použijte jako jakékoli jiné statické pole. Data v poli je jedinečné pro každé vlákno, která ji používá.  
  
 Statická pole relativní vůči vláknu poskytovat lepší výkon než datové sloty ve vztahu a přináší výhody kontrola typu v době kompilace.  
  
 Mějte na paměti, že jakýkoli kód konstruktoru třídy poběží na první vlákno v rámci první, který přistupuje k poli. Ve všech ostatních vláken nebo kontextů ve stejné doméně aplikace, pole bude inicializována tak `null` (`Nothing` v jazyce Visual Basic) Pokud jsou typy odkazů, nebo na jejich výchozí hodnoty, pokud jsou typy hodnot. Proto byste neměli vycházet konstruktor třídy inicializovat statická pole relativní vůči vláknu. Místo toho vyhnout inicializace statická pole relativní vůči vláknu a předpokládá, že jsou inicializovány na hodnotu `null` (`Nothing`) nebo na výchozí hodnoty.  
  
## <a name="data-slots"></a>Datové sloty ve vztahu  
 Rozhraní .NET Framework poskytuje dynamické datové sloty ve vztahu, které jsou jedinečné pro kombinaci vlákna a domény aplikace. Existují dva typy datové sloty ve vztahu: s názvem slotů a nepojmenované sloty. Obě jsou implementovány pomocí <xref:System.LocalDataStoreSlot> struktury.  
  
-   Chcete-li vytvořit slot s názvem data, použijte <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> metody. Pokud chcete získat odkaz na existující slot s názvem, předat její název na <xref:System.Threading.Thread.GetNamedDataSlot%2A> metody.  
  
-   Chcete-li vytvořit nepojmenované datové oblasti, použijte <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> metody.  
  
 Pro obě pojmenované a nepojmenované sloty, použijte <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> metody pro nastavení a načtení informací ve slotu. Toto jsou statické metody, které vždy práci s daty pro vlákno, které je právě probíhá.  
  
 Pojmenované sloty může být vhodné, protože slotu můžete získat až ji budete potřebovat předáním její název na <xref:System.Threading.Thread.GetNamedDataSlot%2A> metoda namísto uchování odkazu na nepojmenovaný slot. Ale pokud jiná komponenta používá stejný název pro své úložiště relativní vůči vláknu a vlákno spustí kód vytvořený z vaší komponentě a další komponenty, dvě součásti může dojít k poškození dat uživatele toho druhého. (Tento scénář předpokládá, že obě komponenty běží ve stejné doméně aplikace, a že nejsou určeny ke sdílení stejná data.)  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ContextStaticAttribute>
- <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>
- <xref:System.ThreadStaticAttribute>
- <xref:System.Runtime.Remoting.Messaging.CallContext>
- [Dělení na vlákna](../../../docs/standard/threading/index.md)

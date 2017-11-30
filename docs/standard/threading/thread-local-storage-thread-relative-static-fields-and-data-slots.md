---
title: "Úložiště vláken Thread Local: statická pole a datové sloty ve vztahu k vláknům"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], local storage
- threading [.NET Framework], thread-relative static fields
- local thread storage
- TLS
ms.assetid: c633a4dc-a790-4ed1-96b5-f72bd968b284
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 39dd80d378171563f2aadadaa146278e8a417d32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="thread-local-storage-thread-relative-static-fields-and-data-slots"></a>Úložiště vláken Thread Local: statická pole a datové sloty ve vztahu k vláknům
Můžete použít spravované úložiště thread local (TLS) k uložení dat které jsou jedinečné pro přístup z více vláken a aplikace domény. Rozhraní .NET Framework poskytuje dva způsoby, jak používat spravované TLS: statická pole a datové sloty relativní vůči vláknu.  
  
-   Použít statická pole relativní vůči vláknu (relativní vůči vláknu `Shared` pole v jazyce Visual Basic) Pokud očekáváte při kompilaci vašim konkrétním potřebám. Statická pole relativní vůči vláknu poskytovat nejlepší výkon. Také vám výhody kontrola typu v kompilaci.  
  
-   Datové sloty ve vztahu použijte, pokud může být zjištěny skutečné požadavky jenom za běhu. Datové sloty ve vztahu je pomalejší a více nevhodných než statická pole relativní vůči vláknu a data se ukládají jako typ <xref:System.Object>, takže musíte vysílat na správný typ dříve, než ho použijete.  
  
 V jazyce C++ nespravované použijete `TlsAlloc` dynamicky přidělit sloty a `__declspec(thread)` deklarovat, že by měla být proměnnou přidělená v relativní vůči vláknu úložiště. Statická pole a datové sloty relativní vůči vláknu zadejte spravovaná verze toto chování.  
  
 V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> třídy za účelem vytvoření místní objekty, které jsou inicializovány líné, když je objekt nejprve zpracován. Další informace najdete v tématu [opožděné inicializace](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="uniqueness-of-data-in-managed-tls"></a>Jedinečnost dat v spravované TLS  
 Jestli používáte statická pole relativní vůči vláknu nebo datové sloty ve vztahu, data ve spravovaných TLS je jedinečná kombinace domény přístup z více vláken a aplikace.  
  
-   V doméně aplikace jedno vlákno nelze upravit data z jiného vlákna, i když obě vlákna používat stejné pole nebo slot.  
  
-   Když vlákno přistupuje k stejné pole nebo slotu z několika domén aplikace, hodnotu samostatné se udržuje v každé doméně aplikace.  
  
 Například pokud je nastaví vlákno hodnotu statická pole relativní vůči vláknu, vstoupí do jiné domény aplikace a pak načte hodnotu pole, hodnota načíst v druhé doméně aplikace se liší od hodnoty v prvním domény aplikace. Nastavením nové hodnoty pro pole v druhé doméně aplikace nemá vliv na hodnotu pole v první domény aplikace.  
  
 Podobně když vlákno získá stejný slot s názvem dat ve dvou různých aplikační domény, data v první doména aplikace zůstane nezávisle na datech v druhé doméně aplikace.  
  
## <a name="thread-relative-static-fields"></a>Statická pole relativní vůči vláknu  
 Pokud víte, že část dat je vždy jedinečné pro přístup z více vláken a kombinace doménu aplikace, budou použity <xref:System.ThreadStaticAttribute> atribut statické pole. Pomocí pole, jako by použít jiné statické pole. Data v poli je jedinečné pro každé vlákno, které ji používají.  
  
 Statická pole relativní vůči vláknu poskytují lepší výkon než datové sloty ve vztahu a mají výhodou kontrola typu v kompilaci.  
  
 Mějte na paměti, všechny kód konstruktoru třídy bude spuštěn na prvním vlákno v první kontextu, který má přístup k poli. Ve všech dalších vláken kontexty ve stejné doméně aplikace, budou inicializována pole na `null` (`Nothing` v jazyce Visual Basic) Pokud jsou odkazové typy, nebo na jejich výchozí hodnoty, pokud jsou hodnoty typů. Proto byste neměli spoléhat na třídu konstruktory k chybě při inicializaci statická pole relativní vůči vláknu. Místo toho vyhnout inicializace statická pole relativní vůči vláknu a předpokládá, že jsou inicializovány pro `null` (`Nothing`) nebo na výchozí hodnoty.  
  
## <a name="data-slots"></a>Datové sloty ve vztahu  
 Rozhraní .NET Framework poskytuje dynamická data sloty, které jsou jedinečné pro kombinaci přístup z více vláken a domény aplikace. Existují dva typy datové sloty ve vztahu: s názvem sloty a nepojmenované sloty. Jak jsou implementované pomocí <xref:System.LocalDataStoreSlot> struktura.  
  
-   Chcete-li vytvořit slot s názvem dat, použijte <xref:System.Threading.Thread.AllocateNamedDataSlot%2A?displayProperty=nameWithType> nebo <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType> metoda. Pokud chcete získat odkaz na existující slot s názvem, předat jeho název <xref:System.Threading.Thread.GetNamedDataSlot%2A> metoda.  
  
-   Chcete-li vytvořit nepojmenované datové oblasti, použijte <xref:System.Threading.Thread.AllocateDataSlot%2A?displayProperty=nameWithType> metoda.  
  
 Pro oba pojmenované a nepojmenované sloty, pomocí <xref:System.Threading.Thread.SetData%2A?displayProperty=nameWithType> a <xref:System.Threading.Thread.GetData%2A?displayProperty=nameWithType> metody nastavit a načíst informace ve slotu. Toto jsou statické metody, které vždy fungovat na základě dat pro vlákno, které je aktuálně spouští.  
  
 Pojmenované sloty může být vhodné, protože přihrádky můžete načíst, pokud budete potřebovat předáním jeho název <xref:System.Threading.Thread.GetNamedDataSlot%2A> metody, místo zachování odkaz na nepojmenované slot. Ale pokud další komponentou používá stejný název pro jeho relativní vůči vláknu úložiště a vlákna spustí kód příslušné součásti a další součásti, dvě součásti může dojít k poškození dat druhé strany. (Tento scénář předpokládá, že obě komponenty běží ve stejné doméně aplikace a že nejsou určený pro sdílení stejná data.)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ContextStaticAttribute>  
 <xref:System.Threading.Thread.GetNamedDataSlot%2A?displayProperty=nameWithType>  
 <xref:System.ThreadStaticAttribute>  
 <xref:System.Runtime.Remoting.Messaging.CallContext>  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)

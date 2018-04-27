---
title: Doplňky a rozšíření
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- extensibility [.NET Framework], add-ins
- add-ins [.NET Framework]
- add-ins [.NET Framework], about
- hosts [.NET Framework], compared to add-ins
- .NET Framework, add-ins
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], compared to hosts
- .NET Framework, extensibility
- versioning [.NET Framework], add-ins
ms.assetid: 8dd45b02-7218-40f9-857d-40d7b98b850b
caps.latest.revision: 42
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e31605f428f4e1dc58ee3332977f14dfd394489
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="add-ins-and-extensibility"></a>Doplňky a rozšíření
<a name="top"></a> Doplňky poskytují rozšířené funkce nebo služby pro hostitelskou aplikaci. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Poskytuje programovací model, který mohou vývojáři k vývoji doplňky a jejich aktivaci ve svých aplikacích hostitele. Model se dosahuje pomocí vytváření komunikační kanál mezi hostitelem a doplněk. Model je implementována pomocí typy v <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, a <xref:System.AddIn.Contract> obory názvů.  
  
 Tento přehled obsahuje následující části:  
  
-   [Model doplňku](#addin_model)  
  
-   [Rozlišit doplňky a hostitele](#distinguishing_between_addins_and_hosts)  
  
-   [Související témata](#related_topics)  
  
-   [Referenční informace](#reference)  
  
> [!NOTE]
>  Další ukázkový kód a zákazník technologie náhledy nástrojů můžete najít pro sestavování doplňku kanály v [spravované rozšiřitelnosti a Framework Add-In lokality na webu CodePlex](http://go.microsoft.com/fwlink/?LinkId=121190).  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a>Model doplňku  
 Model add-in se skládá z řady segmentů, které tvoří doplněk kanálu (také označované jako kanálu komunikace), která je zodpovědná za veškerou komunikaci mezi doplněk a hostitelem. Zřetězení příkazů je symetrický komunikační model segmentů, které výměnu dat mezi-in a jeho hostitele. Vývoj tyto segmenty mezi hostitelem a doplněk poskytuje požadované vrstvy abstrakce, které podporují správu verzí a izolace add-in.  
  
 Následující obrázek znázorňuje kanálu.  
  
 ![Přidat&#45;ve model kanálu. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Kanál doplňku  
  
 Sestavení pro tyto segmenty nejsou nemusí být ve stejné doméně aplikace. Doplněk můžete načíst do své vlastní nové aplikace domény, do existující domény aplikace nebo i do domény aplikace hostitele. Více add in můžete načíst do stejné domény aplikace, která umožňuje doplňků sdílet prostředky a kontexty zabezpečení.  
  
 Model doplňku podporuje a doporučuje hranici volitelné mezi hostitelem a doplněk, který se označuje jako hranic izolace (také označované jako hranici vzdálené komunikace). Tuto hranici může být hranice aplikace domény nebo proces.  
  
 Segment kontrakt uprostřed kanálu je načten do domény aplikace hostitele i v doplňku na domény aplikace. Kontrakt definuje virtuální metody, které hostitele a používání doplňku pro výměnu typy mezi sebou.  
  
 Předávat hranici izolace, musí být typy smluv nebo Serializovatelné typy. Typy, které nejsou kontrakty nebo Serializovatelné typy musí být převést na kontrakty adaptér segmentů v kanálu.  
  
 Zobrazení segmentů kanálu je abstraktní základní třídy nebo rozhraní, které poskytují hostitele a doplněk zobrazení metody, které sdílejí, podle definice kontraktu.  
  
 Další informace o vývoji kanálu segmenty najdete v tématu [vývoj kanálu](../../../docs/framework/add-ins/pipeline-development.md).  
  
 Následující části popisují funkce doplňku modelu.  
  
### <a name="independent-versioning"></a>Nezávislé Správa verzí  
 Model add-in umožňuje hostitelů a doplňky verzi nezávisle. V důsledku toho model add-in umožňuje následující scénáře:  
  
-   Vytvoření adaptér, který umožňuje hostitele použít doplněk vytvořené pro předchozí verze hostitele.  
  
-   Vytvoření adaptér, který umožňuje hostitele použít doplněk vytvořené pro novější verze hostitele.  
  
-   Vytváření adaptér, který umožňuje hostitel používat doplňky vytvořené pro jiného hostitele.  
  
### <a name="discovery-and-activation"></a>Zjišťování a aktivace  
 Doplněk, můžete aktivovat pomocí tokenu z kolekce, která představuje doplňků nalezených v úložišti informace. Doplňky najdete vyhledáním typ, který definuje zobrazení hostitele add-in. Můžete také získat konkrétní doplněk podle typu, který definuje doplněk. Úložiště informací se skládá ze dvou souborů z mezipaměti: kanálu store a Windows store.  
  
 Informace o aktualizaci a znovu sestavit úložiště informací najdete v tématu [Add-in zjišťování](http://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421). Informace o aktivaci doplňků najdete v tématu [aktivace Add-in](http://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) a [postupy: Aktivace doplňky s jinou izolace a zabezpečení](http://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="isolation-levels-and-external-processes"></a>Úrovně izolace a externí procesy  
 Model doplňku podporuje několik úrovní izolace mezi-in a jeho hostitel nebo mezi doplňků. Od nejméně izolované, tyto úrovně jsou následující:  
  
-   Doplněk běží ve stejné doméně aplikace jako hostitel. Není doporučeno, protože ztratíte izolace a uvolnění možnosti, které jste získali při použití různých aplikační domény.  
  
-   Více doplňky jsou načteny do stejné domény aplikace, které se liší od domény aplikace používá hostitel.  
  
-   Každý doplněk načíst výhradně do vlastní domény aplikace. Toto je nejběžnější úroveň izolace.  
  
-   Více doplňky jsou načteny do stejné domény aplikace v externím procesu.  
  
-   Každý doplněk načíst výhradně do vlastní domény aplikace v externím procesu. Toto je nejvíce izolované scénář.  
  
 Další informace o použití externí procesů najdete v tématu [postupy: Aktivace doplňky s jinou izolace a zabezpečení](http://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="lifetime-management"></a>Správa po dobu platnosti  
 Vzhledem k tomu, že model doplňku zahrnuje aplikace domény a proces hranice, uvolňování paměti sám o sobě není dostatečná pro verzi a uvolnění objektů. Model doplňku poskytuje mechanismus správy životního cyklu, který používá tokeny a počítání odkazů a obvykle nevyžaduje další programování. Další informace najdete v tématu [správu životního cyklu](http://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
 [Zpět na začátek](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a>Rozlišit doplňky a hostitele  
 Rozdíl mezi-v a hostitele je jenom hostitel je ten, který aktivuje v doplňku. Hostiteli může být větší dvou, jako je například aplikace word zpracování a jeho programy pro kontrolu pravopisu; nebo hostitele může být menší ze dvou, jako je například klienta rychlého zasílání zpráv, který se vloží přehrávač médií. Model doplňku podporuje doplňky ve scénářích klient i server. Příklady doplňky serveru zahrnují doplňky, které poskytují poštovních serverů s vyhledáváním virů, filtry nevyžádané pošty a ochranu IP. Klient doplňku příklady zahrnují doplňky odkaz pro textové editory, specializované funkce grafických aplikací a her a pro místní e-mailové klienty pro vyhledávání virů.  
  
 [Zpět na začátek](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Vývoj kanálu](../../../docs/framework/add-ins/pipeline-development.md)|Popisuje komunikační kanál segmentů z hostitelskou aplikaci pro doplněk. Obsahuje příklady kódu v tématech návod, které popisují, jak k vytvoření kanálu a jak nasadit segmenty do kanálu v sadě Visual Studio.|  
|[Domény a sestavení aplikací](http://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)|Popisuje vztah mezi doménami aplikací, které poskytují hranici izolace zabezpečení, spolehlivosti a správa verzí a sestavení.|  
  
 [Zpět na začátek](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [Zpět na začátek](#top)
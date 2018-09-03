---
title: Doplňky a rozšíření
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb2485f2ecf0426360dba80d443500a92b5a7af6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482220"
---
# <a name="add-ins-and-extensibility"></a>Doplňky a rozšíření
<a name="top"></a> Doplňky poskytují rozšířené funkce nebo služby pro hostitelskou aplikaci. [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Poskytuje programovací model, který mohou vývojáři k vývoji doplňky a aktivovat ve své hostitelské aplikaci. Model toho dosahuje tak, že vytváří komunikační kanál mezi hostitelem a doplňku. Model je implementovaný s využitím typy v <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, a <xref:System.AddIn.Contract> obory názvů.  
  
 Tento přehled obsahuje následující části:  
  
-   [Přidání modelu](#addin_model)  
  
-   [Rozlišování mezi moduly a hostiteli](#distinguishing_between_addins_and_hosts)  
  
-   [Související témata](#related_topics)  
  
-   [Referenční informace](#reference)  
  
> [!NOTE]
>  Další ukázky kódu a náhledy technologie zákazníka nástrojů můžete najít pro vytváření doplňku kanály na [Managed Extensibility a přidat v rámci webu na webu CodePlex](https://go.microsoft.com/fwlink/?LinkId=121190).  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a>Přidání modelu  
 Model doplňku se skládá z řady segmenty, které tvoří doplňku kanálu (označované také jako komunikační kanál), která zodpovídá za veškerou komunikaci mezi doplněk a hostitelem. Kanál je symetrické komunikační model segmentů, které výměnu dat mezi doplňkem a jeho hostitelem. Vývoj těchto segmentů mezi hostitelem a doplněk poskytuje požadovaných úrovní abstrakce, které podporují správu verzí a izolaci doplňku.  
  
 Následující obrázek ukazuje kanál.  
  
 ![Přidat&#45;v kanálu modelu. ](../../../docs/framework/add-ins/media/addin1.png "AddIn1")  
Kanál doplňku  
  
 Sestavení pro tyto segmenty nejsou musí být ve stejné doméně aplikace. Do své vlastní nové aplikační doméně, do existující domény aplikace nebo dokonce do domény aplikace hostitele můžete načíst doplněk. Načtení více doplňků do stejné doméně aplikace, která umožňuje doplňky sdílet prostředky a kontext zabezpečení.  
  
 V modelu doplňku podporuje a doporučuje, abyste, volitelné hranice mezi hostitelem a doplněk, který se nazývá oddělovací hranice (označované také jako hranice vzdálené komunikace). Toto rozhraní může být hranice domény nebo proces aplikace.  
  
 Segment smlouvy uprostřed kanálu se načtou do domény aplikací hostitele a doplněk na aplikační domény. Kontrakt definuje virtuální metody, které hostitele a používání doplňku pro výměnu typy mezi sebou.  
  
 Předávání oddělovací hranice, musí být typy kontraktů nebo Serializovatelné typy. Typy, které nejsou smluv nebo Serializovatelné typy musí být převeden na smlouvy adaptér segmenty v kanálu.  
  
 Zobrazení segmentů kanálu jsou abstraktní základní třídy nebo rozhraní, které poskytují hostitele a doplňku zobrazení metody, které sdílejí, jak je definováno ve smlouvě.  
  
 Další informace o vývoji segmenty kanálu najdete v tématu [vývoj kanálu](../../../docs/framework/add-ins/pipeline-development.md).  
  
 Následující části popisují funkce modelu doplňku.  
  
### <a name="independent-versioning"></a>Nezávislé správy verzí  
 Model doplňku umožňuje hostiteli a doplňky na verzi nezávisle na sobě. V důsledku toho model doplňku umožňuje následující scénáře:  
  
-   Vytvoření adaptéru, který umožňuje hostitele doplňku vytvořené pro předchozí verzi hostitele.  
  
-   Vytvoření adaptéru, který umožňuje hostitele doplňku vytvořené pro novější verzi hostitele.  
  
-   Vytvoření adaptéru, který umožňuje hostitele doplňky vytvořené pro jiného hostitele.  
  
### <a name="discovery-and-activation"></a>Zjišťování a aktivace  
 Doplněk můžete aktivovat pomocí tokenu z kolekce, která představuje doplňky od úložiště informace. Doplňky se nacházejí tak, že typ, který definuje hostitelském zobrazení doplňku. Můžete také najít konkrétní doplňku podle typu, který definuje doplňku. Informace o úložišti se skládá ze dvou souborů z mezipaměti: úložiště kanálu a ve storu.  
  
 Informace o aktualizace a opětovné vytvoření úložiště informací najdete v tématu [doplňky zjišťování](https://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421). Informace o aktivaci doplňky, naleznete v tématu [Add-in aktivace](https://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) a [postupy: Aktivace doplňků s různou úrovní izolace a zabezpečení](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="isolation-levels-and-external-processes"></a>Úrovně izolace a externí proces  
 Model doplňku podporuje několik úrovní izolace mezi doplňkem a jeho hostitelem nebo doplňky. Od nejméně izolované, tyto úrovně jsou následující:  
  
-   Doplněk běží ve stejné doméně aplikace jako hostitele. To se nedoporučuje, protože ztratíte izolace a uvolnění možnosti, které získáte při použití různých aplikačních doménách.  
  
-   Více moduly se načítají do stejné domény aplikace, které se liší od aplikační domény, používá hostitel.  
  
-   Každý doplněk načten výhradně na vlastní doménu aplikace. Toto je nejběžnější úroveň izolace.  
  
-   Více doplňky jsou načtena do stejné domény aplikace v externím procesu.  
  
-   Každý doplněk načten výhradně na vlastní doméně aplikace v externím procesu. Toto je nejčastěji izolované scénář.  
  
 Další informace o používání externí proces, naleznete v tématu [postupy: Aktivace doplňků s různou úrovní izolace a zabezpečení](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).  
  
### <a name="lifetime-management"></a>Správa po dobu platnosti  
 Protože model doplňku přesahuje hranice aplikační domény a proces, uvolňování paměti sám o sobě není dostatečná k vydání verze a uvolnění objektů. Model doplňku poskytuje mechanismus správy životního cyklu, které používá tokeny a počítání odkazů a obvykle nevyžaduje další programování. Další informace najdete v tématu [Správa životního cyklu](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).  
  
 [Zpět na začátek](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a>Rozlišování mezi moduly a hostiteli  
 Rozdíl mezi doplňkem a hostitelem je pouze, že hostitel je ten, který aktivuje doplněk. Hostitel může být větší z nich, jako je zpracování textu aplikace a její pravopisu; nebo může být menší z nich, jako je rychlé klienta zasílání zpráv, který vloží multimediální přehrávač hostitele. Model doplňku podporuje doplňků ve scénářích klienta i serveru. Doplňky server příklady doplňků, které poskytují poštovních serverů s vyhledávání virů, filtry nevyžádané pošty a ochranu IP. Klient doplněk mezi příklady patří referenční doplňky textových editorů, specializované funkce grafických aplikací a her a virů pro místní e-mailoví klienti.  
  
 [Zpět na začátek](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Vývoj kanálu](../../../docs/framework/add-ins/pipeline-development.md)|Popisuje komunikační kanál segmenty z hostitelské aplikace doplňku. Poskytuje příklady kódu v návody, které popisují, jak k vytvoření kanálu a jak nasadit segmentů kanálu v sadě Visual Studio.|  
|[Domény a sestavení aplikací](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)|Popisuje relace mezi doménami aplikace, které poskytují izolační hranici pro zabezpečení, spolehlivosti a správy verzí a sestavení.|  
  
 [Zpět na začátek](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [Zpět na začátek](#top)
---
title: Přehled manipulace a nečinnosti
ms.date: 03/30/2017
ms.assetid: dd31b89b-eab6-45a1-8d0b-11e0eb84b234
ms.openlocfilehash: 7aec2756bfc3a7d4ccd394d54f19428d73b44fcb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32744392"
---
# <a name="manipulations-and-inertia-overview"></a>Přehled manipulace a nečinnosti
*Manipulace* povolit uživatelům přesunout, otáčení a změna velikosti prvky uživatelského rozhraní (UI) pomocí *manipulátory*. Manipulator představuje myši nebo (v případě dotykovým ovládáním) pera nebo prstu.  
  
 *Nečinnosti* emuluje chování skutečných pro prvky uživatelského rozhraní, které jsou v provozu tak, že simuluje třecí vynutí u elementů. To umožňuje elementy postupně zpomalit jejich přesun (lineární i úhlová) před přicházející na určeném místě. Tento článek obsahuje úvod do manipulace a nečinnosti pro rozhraní .NET Framework.  
  
## <a name="manipulations"></a>Manipulace  
 Manipulaci s kolekce manipulátory považuje za složeného objektu. Aplikace můžete sledovat změny složeného objektu místo individuálních komponent.  
  
 Vezměte v úvahu bitovou kopii na následujícím obrázku. Uživatele můžete použít dva manipulátory přesunout, otáčení a změna měřítka obrázku. Změny se každý manipulator vyhodnocovány společně s jiné manipulátory.  
  
 Například, pokud máte dva manipulátory (1 a 2) na bitovou kopii a přesunout manipulator 1 v + směru osy Y (dolů), tato změna bitovou kopii, závisí na co se stane manipulator 2. Pokud manipulator 2 přesune také v + směru osy Y (dolů), bitovou prochází jednoduše + směru osy Y. Ale pokud manipulator 2 se nemění, nebo ji přesune směrem -Y (si), je menší nebo otočený provedené bitovou kopii.  
  
 ![Virtuální fotografie, který dva prsty, které jsou manipulace s nimi. ] (../../../docs/framework/common-client-technologies/media/manipulation-resize.png "Manipulation_Resize")  
  
 Obrázek se manipulovat dvě manipulátory  
  
 Manipulace s zpracování poskytuje rozhraní, které monitoruje podmnožinu manipulátory a je interpretuje jako kdyby jejich fungují společně, namísto nezávisle. Můžete vytvořit několik manipulaci s objekty procesoru současně, jednu pro jednotlivé elementy uživatelského rozhraní pro upravit v aplikaci. Manipulace s procesoru je informováni o kterém vstupní zařízení pro sledování a oznámí manipulace prostřednictvím [.NET události](http://msdn.microsoft.com/library/17sde2xt.aspx).  
  
 Manipulace s procesor nemá informace o konkrétní elementu, který je právě zpracovávaného. Aplikace samostatně použije změny na element specifické pro aplikaci. Například aplikace použije transformace na bitovou kopii nebo ho překreslí ho zobrazte jej v jeho novém umístění nebo s novou velikost nebo orientace.  
  
 Manipulace jsou navrženy pro dvourozměrná (2-D) [afinní transformace](http://msdn.microsoft.com/library/ms533810\(VS.85\).aspx). Zahrnout tyto transformace převede, otáčení a škálování.  
  
### <a name="parts-of-a-manipulation"></a>Součásti manipulace  
 Manipulaci s je kolekce <xref:System.Windows.Input.Manipulations.Manipulator2D> objekty. Tento agregační manipulaci s představuje bod počátku a elipsy. Počáteční bod je průměrná pozice všech manipulátory, které jsou manipulace s elementu. Má se třemi tečkami radius, který je průměrná vzdálenost od počátku ke každému <xref:System.Windows.Input.Manipulations.Manipulator2D> objekty.  
  
 ![Části manipulaci s. ] (../../../docs/framework/common-client-technologies/media/manipulation-definition.png "Manipulation_Definition")  
  
 Dva manipulátory (1 a 2), počátek a elipsy zadejte manipulaci s  
  
 Jako manipulátory se přidají, přesunout nebo odeberou pro element uživatelského rozhraní, aplikaci aktualizací <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> objekt voláním <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> metoda. Po první zahájení manipulaci <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> událost se vyvolá.  
  
> [!NOTE]
>  Manipulace s zpracování je efektivnější při použití v prostředí na základě rámce aktualizace. Při použití manipulace zpracování v aplikaci Microsoft XNA, to není důležité, protože rozhraní XNA framework poskytuje na základě rámce aktualizací pomocí [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) metoda. V jiné prostředí (například WinForms), může být nutné zadat vlastní logiky na základě rámce pro shromažďování manipulace a pošlete je pravidelně <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> metoda jako dávku.  
  
 Jako počet manipulátory nebo změnit jejich pozici <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> událost se vyvolá. Vlastnosti <xref:System.Windows.Input.Manipulations.Manipulation2DDeltaEventArgs> objekt, který je předán <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> obslužné rutiny události zadejte změny v původu, měřítko, otáčení a překlad, ke kterým došlo od poslední události. Původ manipulaci se změní při manipulátory přesunout, a při přidávání nebo odebírání manipulátory. Překlad hodnoty určují, kolik X nebo Y přesun obsahuje manipulaci.  
  
 Pomocí nových hodnot, aplikace ho překreslí element uživatelského rozhraní.  
  
 ![Manipulace s po kontaktu A přesunout vpravo. ] (../../../docs/framework/common-client-technologies/media/manipulation-changed.png "Manipulation_Changed")  
  
 Manipulator 1 přesune a způsobí, že počátek změnit  
  
 Po odebrání poslední manipulator, který je přidružen manipulaci z <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> objekt, <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> událost se vyvolá.  
  
### <a name="the-manipulation-processing-model"></a>Manipulace s zpracování modelu  
 Manipulace s procesor používá model přímého využití. Pomocí tohoto jednoduchého modelu musí aplikace předat žádné podrobnosti vstupní události procesoru manipulaci. Vstupní událost může být aktivováno žádný vstup primitivní, jako je například zařízení myši, pera nebo prstem. Tento proces zajišťuje přímé filtrační mechanismus a jednoduché použití modelu, tak může aplikace batch vstupní události v případě potřeby.  
  
 Pro aplikace, aby zahrnovala vstupní primitivní v procesu manipulaci, vytvoří <xref:System.Windows.Input.Manipulations.Manipulator2D> struktura z podrobností o vstupní primitivní a předává strukturu pro manipulaci s procesor používá <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> metoda. Manipulace s procesoru poté vyvolá události, které aplikace musí zpracovat aktualizace visual component vhodným způsobem.  
  
 ![Tok přímá manipulace&#45;modelu využití. ] (../../../docs/framework/common-client-technologies/media/manipulation-flow.png "Manipulation_Flow")  
  
 Manipulace s zpracování modelu  
  
## <a name="inertia"></a>Nečinnosti  
 Nečinnosti procesoru umožňuje aplikacím odvodit umístění, orientaci a další vlastnosti prvku uživatelského rozhraní tak, že simuluje reálného chování.  
  
 Například když uživatel rychlých pohybů element, ho můžete pokračovat přesunutí, zpomalení a pomalu zastavit. Afinní 2-D hodnot (původu, škálování, překlad a otočení) Chcete-li změnit přes určitou dobu v zadané zpomalení nečinnosti procesoru implementuje toto chování.  
  
 Jako s zpracování manipulaci nečinnosti procesoru nemá informace o všech určitý element uživatelského rozhraní. V reakci na události, které jsou vyvolány na <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> objektu, aplikaci samostatně použije změny na element specifické pro aplikaci.  
  
 Zpracování manipulace a nečinnosti zpracování se často používají společně. Rozhraní jsou podobné a události, které vyvolají (v některých případech) identické. Obecně platí začne nečinnosti zpracování po dokončení zpracování elementu uživatelského rozhraní. To lze provést naslouchá <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> událostí a spuštění nečinnosti zpracování z této obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Input.Manipulations>

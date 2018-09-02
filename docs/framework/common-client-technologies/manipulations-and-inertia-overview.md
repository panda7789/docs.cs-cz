---
title: Přehled manipulace a nečinnosti
ms.date: 03/30/2017
ms.assetid: dd31b89b-eab6-45a1-8d0b-11e0eb84b234
ms.openlocfilehash: 41c22dc305f8ef653705436544ab2342e55ed02a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43401222"
---
# <a name="manipulations-and-inertia-overview"></a>Přehled manipulace a nečinnosti
*Manipulace* povolit uživatelům přesunout, otočit a změnit velikost prvky uživatelského rozhraní (UI) s použitím *manipulátory*. Manipulátor představuje myši nebo (v případě dotykově ovládaný) stylus nebo prstem.  
  
 *Nečinnost* emuluje chování skutečných pro prvky uživatelského rozhraní, které jsou přenášená data pomocí simulace vynutí řešit zádrhele spojené s prvky. To umožňuje prvků, které se postupně zpomalit jejich přesunu (lineární a angular) před přicházející na zarážku. Tento článek obsahuje úvod do manipulace a nečinnosti pro rozhraní .NET Framework.  
  
## <a name="manipulations"></a>Manipulace  
 Manipulaci s považuje kolekce manipulátory složeného objektu. Aplikace můžete sledovat změny složeného objektu namísto jednotlivých komponent.  
  
 Vezměte v úvahu bitovou kopii na následujícím obrázku. Uživatele můžete použít dvě manipulátory přesunout, otáčet a změna měřítka obrázku. Změny se každý manipulátor jsou interpretovány společně s další manipulátory.  
  
 Například, pokud máte dva manipulátory (1 a 2) na obrázku a přesunout manipulátor 1 v + směru osy Y (dolů) změny do bitové kopie závisí na co se stane manipulátor 2. Pokud manipulátor 2 také přesune + směru osy Y (dolů), image jednoduše přesune + směru osy Y. Ale pokud manipulátor 2 nedojde ke změně nebo přesunu ve směru -Y (nahoru), na obrázku je menší nebo otočený.  
  
 ![Virtuální fotografie, se dvěma prsty manipulaci. ](../../../docs/framework/common-client-technologies/media/manipulation-resize.png "Manipulation_Resize")  
  
 Obrázek se manipulovat dvě manipulátory  
  
 Manipulace s zpracování poskytuje architekturu, která monitoruje podmnožinu manipulátory a interpretuje je, jako kdyby jejich fungují společně, namísto nezávisle na sobě. Můžete vytvořit několik manipulaci s objekty procesoru současně, jeden pro každý prvek uživatelského rozhraní na manipulovat v aplikaci. Manipulace s procesor je informován o kterém vstupní zařízení pro sledování a sestavy manipulace prostřednictvím [události .NET](https://msdn.microsoft.com/library/17sde2xt.aspx).  
  
 Procesor manipulaci s nemá žádné informace o konkrétní elementu, který je právě zpracováván. Změny aplikace samostatně platí pro konkrétní aplikaci prvku. Například aplikace použije transformace pro bitovou kopii nebo jej chcete zobrazit v jeho novém umístění nebo s novou velikost nebo orientaci překreslí.  
  
 Manipulace jsou určeny pro dvojrozměrné (2-D) [afinní transformace](/windows/desktop/gdiplus/-gdiplus-transformations-use). Zahrnout tyto transformace přeložit, otočit a škálovat.  
  
### <a name="parts-of-a-manipulation"></a>Součásti manipulace  
 Manipulaci s je kolekce <xref:System.Windows.Input.Manipulations.Manipulator2D> objekty. Tato agregace manipulace představuje počáteční bod a elipsu. Počáteční bod je průměrná pozice všech manipulátory, které jsou zpracování elementu. Protokolu radius, který je průměrná vzdálenost od počátku na každý má tři tečky <xref:System.Windows.Input.Manipulations.Manipulator2D> objekty.  
  
 ![Části manipulaci s. ](../../../docs/framework/common-client-technologies/media/manipulation-definition.png "Manipulation_Definition")  
  
 Dva manipulátory (1 a 2), původ a elipsa zadejte manipulaci s  
  
 Manipulátory jsou přidávání, přesunout a odebírání pro prvek uživatelského rozhraní, aplikace aktualizuje <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> objektu voláním <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> metody. Po prvním zahájení manipulace <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> událost se vyvolá.  
  
> [!NOTE]
>  Manipulace s zpracování je mnohem efektivnější, při použití v prostředí založených na snímcích aktualizace. Při použití manipulace s zpracování v aplikaci Microsoft XNA, to není žádný problém vzhledem k tomu, že poskytuje založených na snímcích aktualizací pomocí rozhraní XNA framework [Game.Update](https://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) metody. V jiném prostředí (například WinForms), musíte poskytnout vlastní logiku založených na snímcích pro shromažďování manipulace a pravidelně jim odesílání <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> metoda v dávce.  
  
 Jako počet manipulátory nebo změnit jejich pozici <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> událost se vyvolá. Vlastnosti <xref:System.Windows.Input.Manipulations.Manipulation2DDeltaEventArgs> objekt, který je předán <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> obslužná rutina události zadejte změny původu, škálování, otočení a překladu, ke kterým došlo od poslední události. Původ manipulace změní, když manipulátory přesunout, a při přidání nebo odebrání manipulátory. Překlad hodnoty určují, kolik X nebo Y přesun obsahuje manipulaci.  
  
 Pomocí nové hodnoty, překreslí aplikaci prvku uživatelského rozhraní.  
  
 ![Manipulace s po kontaktu A přesunout na pravé straně. ](../../../docs/framework/common-client-technologies/media/manipulation-changed.png "Manipulation_Changed")  
  
 Manipulátor 1 přesune a způsobí, že původní změna  
  
 Při poslední manipulátor, který je přidružený k manipulaci se odebere z <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> objektu, <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> událost se vyvolá.  
  
### <a name="the-manipulation-processing-model"></a>Manipulace s zpracování modelu  
 Manipulace s procesor používá model přímého využití. Pomocí tohoto jednoduchého modelu musí aplikace předat všechny podrobnosti o vstupní události zpracování procesoru. Vstupní události může být vyvolána zadáním primitivní, jako je například zařízení myši, stylus nebo prstem. Tento proces zajišťuje mechanismus filtrování s přímým přístupem a modelu využití jednoduché, tak můžete aplikace batch vstupní události v případě potřeby.  
  
 Pro aplikace, aby zahrnovala vstupní primitivní v manipulaci s procesem, vytvoří <xref:System.Windows.Input.Manipulations.Manipulator2D> struktury z podrobností vstupních primitivní vlastnost a předává struktury k manipulaci s pomocí procesoru <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.ProcessManipulators%2A> metoda. Manipulace s procesoru poté vyvolá události, které aplikace musí zpracovat aktualizovat komponentu visual vhodným způsobem.  
  
 ![Tok přímé manipulace&#45;modelu využití. ](../../../docs/framework/common-client-technologies/media/manipulation-flow.png "Manipulation_Flow")  
  
 Manipulace s zpracování modelu  
  
## <a name="inertia"></a>Nečinnosti  
 Nečinný procesor umožňuje aplikacím budete jen simulovat skutečné chování potom údaje extrapolovat umístění, orientace a další vlastnosti prvku uživatelského rozhraní.  
  
 Například když uživatel rychlých pohybů elementu, může pokračovat v pohybu, zpomalení a pomalu zastavit. Nečinný procesor implementuje toto chování způsobením nastavená na affine 2D hodnoty (původu, škálování, překlad a otočení) Chcete-li změnit za určitou dobu v zadané zpomalení.  
  
 Jako zpracování manipulaci s nečinný procesor nemá žádné informace o žádné konkrétní prvek uživatelského rozhraní. V reakci na události, které jsou vyvolány na <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> objektu aplikace samostatně změny použije na konkrétní aplikaci prvku.  
  
 Zpracování manipulace a nečinnost zpracování se často používá společně. Jsou podobné jejich rozhraní a (v některých případech) jsou události, které vyvolají identické. Obecně platí zpracování nečinnost začíná, když se dokončí zpracování prvek uživatelského rozhraní. To lze provést prostřednictvím naslouchání <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> události a spouštění nečinnost zpracování z této obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Input.Manipulations>

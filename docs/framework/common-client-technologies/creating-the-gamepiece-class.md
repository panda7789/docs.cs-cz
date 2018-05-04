---
title: Vytvoření třídy GamePiece
ms.date: 03/30/2017
ms.assetid: 37a27a86-ac1c-47be-b477-cb4b819459d3
ms.openlocfilehash: 0939da6eca579bd030bfe18b24d8364fbcc4fc82
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="creating-the-gamepiece-class"></a>Vytvoření třídy GamePiece
**GamePiece** třída zapouzdří všechny funkce, které jsou potřebné k načtení bitovou kopii Microsoft XNA herní část, sledovat stav myši ve vztahu k herní část, zachycení myši, zadejte manipulace a nečinnosti zpracování, a Když herní část dosáhne omezení zobrazení port, zadejte skákající schopnosti.  
  
## <a name="private-members"></a>Soukromé členy  
 V horní části **GamePiece** třídy, jsou deklarovány několik soukromé členy.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privatemembers)]  
  
## <a name="public-properties"></a>Veřejné vlastnosti  
 Tři z těchto soukromé členy se zveřejňují přes veřejné vlastnosti. **Škálování** a **PieceColor** vlastnosti povolení aplikace k určení, měřítko a barvu část, v uvedeném pořadí. **Hranice** je vlastnost k dispozici povolit jednu část chcete použít k vykreslení samostatně, například když jedna část by měl překrytí jiný rozsah jiného. Následující kód ukazuje deklaraci veřejných vlastností.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PublicProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_publicproperties)]  
  
## <a name="class-constructor"></a>Třída – konstruktor  
 V konstruktoru pro **GamePiece** třída přijímá následující parametry:  
  
-   A [SpriteBatch](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.aspx) typu. Odkaz na předán zde je přiřazena k privátního člena `spriteBatch`a slouží pro přístup k [SpriteBatch.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.draw.aspx) metoda při herní část vykreslí sám sebe. Kromě toho [GraphicsDevice](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.spritebatch.graphicsdevice.aspx) vlastnost se používá k vytvoření [Texture](http://msdn.microsoft.com/library/microsoft.xna.framework.graphics.texture.aspx) objekt související s herní část a získat velikost zobrazení portu, aby bylo možné rozpoznat, kdy se zaznamená herní část okno hranic tak, aby na požadovaný můžete kolísají.  
  
-   Řetězec, který určuje název souboru obrázku pro herní část.  
  
 V konstruktoru vytvoří také <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> objektu a <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> objektu a vytvoří obslužné rutiny události pro svoje události.  
  
 Následující kód ukazuje v konstruktoru pro **GamePiece** třídy.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Constructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_constructor)]  
  
## <a name="capturing-mouse-input"></a>Zachytávání vstupu myší  
 **UpdateFromMouse** metoda je zodpovědná za vyhledávání podpory při stisknutí tlačítka myši, myš není v rámci hranic herní část a pro zjišťování při uvolnění tlačítka myši.  
  
 Při stisknutí levé tlačítko myši (při, myš není uvnitř hranice část), tato metoda nastaví příznak označující, že tento herní část má zachycení myši a zahájí zpracování manipulaci s.  
  
 Manipulace s zpracování spuštěna vytvořením pole <xref:System.Windows.Input.Manipulations.Manipulator2D> objekty a jejich předání <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> objektu. To způsobí, že manipulaci s procesor pro vyhodnocení manipulátory (v tomto případě jednom manipulator) a vyvolávání událostí manipulaci.  
  
 Kromě toho je bod, ve kterém dochází k přetahování uložit. Používá se později v průběhu <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> událostí upravit překlad rozdílové hodnoty tak, aby herní část přenáší v souladu se za bod přetažení.  
  
 Nakonec tato metoda vrátí stavu zaznamenání myši. Díky tomu [GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) objekt, který chcete spravovat, zaznamenávání po herní na více místech.  
  
 Následující kód ukazuje **UpdateFromMouse** metoda.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_updatefrommouse)]  
  
## <a name="processing-manipulations"></a>Zpracování manipulace  
 Po zahájení zpracování <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> událost se vyvolá. Obslužná rutina pro tuto událost zastaví nečinnosti zpracování, pokud dochází a nastaví *processInertia* příznak, který `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationStarted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationstarted)]  
  
 Jako hodnoty přidružené k manipulaci s změnu <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> událost se vyvolá. Obslužná rutina pro tuto událost používá rozdílové hodnoty předávané události argumenty změnit na pozici a oběh hodnoty herní část.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationdelta)]  
  
 Když jsou odebrány všechny položky manipulátory (v tomto případě jednom manipulator), které jsou přidruženy manipulaci, vyvolá zpracování procesoru <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> událostí. Obslužná rutina pro tuto událost začne nečinnosti zpracování nastavením počáteční jsou rychlosti procesoru nečinnosti těm, které jsou uvedeny argumenty událostí a nastaví *processInertia* příznak, který `true`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationcompleted)]  
  
## <a name="processing-inertia"></a>Zpracování nečinnosti  
 Jako zpracování nečinnosti extrapolates nové hodnoty pro úhlová a lineární jsou rychlosti, souřadnice polohy (překlad) a otáčení <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> událost se vyvolá. Obslužná rutina pro tuto událost používá rozdílové hodnoty předávané události argumenty změnit pozice a oběh herní část.  
  
 Pokud nové souřadnice povedou herní část přesun mimo hranice port zobrazení, má obrácený rychlosti zpracování nečinnosti. To způsobí, že herní část kolísají mimo hranice port zobrazení, která byla zjištěna.  
  
 Nelze změnit vlastnosti <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> objektu, když je spuštěná extrapolace. Proto když Prohodit rychlosti X nebo Y, obslužné rutiny události nejprve zastaví nečinnosti voláním <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Complete%2A> metoda. Potom přiřadí nové rychlosti počáteční hodnoty, které mají být aktuální hodnoty rychlosti (přizpůsobené pro chování houba) a nastaví *processInertia* příznak, který `true`.  
  
 Následující kód ukazuje obslužné rutiny události pro <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> událostí.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiadelta)]  
  
 Po dokončení zpracování nečinnosti procesoru nečinnosti vyvolá <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Completed> událostí. Nastaví obslužnou rutinu pro tuto událost *processInertia* příznak, který `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiacompleted)]  
  
 Žádná z logiky zobrazí, pokud ve skutečnosti způsobí nečinnosti extrapolace proběhnout. To lze provést v **ProcessInertia** metoda. Tuto metodu, která se nazývá opakovaně smyčky herní aktualizace ( [Game.Update](http://msdn.microsoft.com/library/microsoft.xna.framework.game.update.aspx) metoda) kontroluje, pokud *processInertia* je příznak nastaven na `true`a pokud ano, zavolá <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Process%2A> Metoda. Volání tato metoda příčiny extrapolace proběhnout a vyvolá <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> událostí.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_ProcessInertia](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_processinertia)]  
  
 Herní část není ve skutečnosti vykreslen, dokud jeden z přetížení metody kreslení se nazývá. První přetížení tato metoda je volána opakovaně smyčky herní kreslení ( [Game.Draw](http://msdn.microsoft.com/library/microsoft.xna.framework.game.draw.aspx) metoda). To vykreslí herní část s aktuální pozici, otáčení a měřítko.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Draw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_draw)]  
  
## <a name="additional-properties"></a>Další vlastnosti  
 Tři privátní vlastnosti jsou používány **GamePiece** třídy.  
  
1.  **Časové razítko** – získá hodnotu časové razítko má být používána procesory manipulace a nečinnosti.  
  
2.  **X** – získá nebo nastaví souřadnici X herní část. Při nastavování, upraví se hranice používána pro testování přístupů a umístění pivot procesoru manipulaci.  
  
3.  **Y** – získá nebo nastaví souřadnici Y herní část. Při nastavování, upraví se hranice používána pro testování přístupů a umístění pivot procesoru manipulaci.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privateproperties)]  
  
## <a name="see-also"></a>Viz také  
 [Manipulace a nečinnost](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Použití manipulace a nečinnosti v aplikaci XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Vytvoření třídy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Vytvoření třídy Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)

---
title: Vytvoření třídy GamePiece
ms.date: 03/30/2017
ms.assetid: 37a27a86-ac1c-47be-b477-cb4b819459d3
ms.openlocfilehash: f9f08437cda685d2ec1d2d0c8d54d370d9d38341
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195876"
---
# <a name="creating-the-gamepiece-class"></a>Vytvoření třídy GamePiece
**GamePiece** třída zapouzdří všechny funkce potřebné k načtení bitové kopie Microsoft XNA game část, sledovat stav myši ve vztahu k her jsou části, zachycení myši, poskytují manipulace a nečinnost zpracování, a skákající možnost poskytnout, herní část dosáhne omezení zobrazení.  
  
## <a name="private-members"></a>Soukromé členy  
 V horní části **GamePiece** několik soukromých členů třídy, jsou deklarovány.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateMembers](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privatemembers)]  
  
## <a name="public-properties"></a>Veřejné vlastnosti  
 Tří z těchto soukromé členy jsou přístupné prostřednictvím veřejných vlastností. **Škálování** a **PieceColor** vlastnosti umožňují aplikaci na určit měřítko a barvy – počítač, v uvedeném pořadí. **Hranice** vlastnost vystavena povolit jednu část hranice jiné použitých k vykreslování, například když jednu část by měla překryv jiného. Následující kód ukazuje deklaraci třídy veřejné vlastnosti.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PublicProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_publicproperties)]  
  
## <a name="class-constructor"></a>Konstruktor třídy  
 Konstruktor pro **GamePiece** třídy přijímá následující parametry:  
  
-   A [SpriteBatch](https://docs.microsoft.com/previous-versions/windows/xna/bb199034%28v%3dxnagamestudio.41%29) typu. Odkazu předaného zde je přiřazena k soukromému členu `spriteBatch`a používá se k přístupu [SpriteBatch.Draw](https://docs.microsoft.com/previous-versions/windows/xna/bb196426%28v%3dxnagamestudio.41%29) metoda při her – počítač se vykreslí. Kromě toho [GraphicsDevice](https://docs.microsoft.com/previous-versions/windows/xna/bb197338%28v%3dxnagamestudio.41%29) vlastnost se používá k vytvoření [textury](https://docs.microsoft.com/previous-versions/windows/xna/bb199375%28v%3xnagamestudio.41%29) objektu souvisejícího s her – počítač a získat velikost zobrazení portu, aby bylo možné rozpoznat, kdy se zaznamená část her okno hranic tak, aby je tímto druhem můžete odraz.  
  
-   Řetězec, který určuje název souboru obrázku používaného pro herní část.  
  
 Konstruktor také vytvoří <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> objektu a <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> objektu a vytvoří obslužné rutiny událostí pro jejich události.  
  
 Následující kód ukazuje konstruktor pro **GamePiece** třídy.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Constructor](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_constructor)]  
  
## <a name="capturing-mouse-input"></a>Zachytávání vstup z myši  
 **UpdateFromMouse** metoda je zodpovědná za vyhledávání podpory při stisknutí tlačítka myši, zatímco ukazatel myši nachází v dané oblasti her – počítač a pro zjišťování, při uvolnění tlačítka myši.  
  
 Při stisknutí levého tlačítka myši (zatímco je ukazatel myši nachází uvnitř hranic část), tato metoda nastaví příznak označující, že část této hry zachytí myš a zahájí zpracování manipulaci s.  
  
 Manipulace s zpracování je tím, že vytvoříte pole <xref:System.Windows.Input.Manipulations.Manipulator2D> objekty a jejich předání <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D> objektu. To způsobí, že procesor manipulaci s vyhodnotit manipulátory (v tomto případě jedné manipulátor) a vyvolat manipulace s událostmi.  
  
 Kromě toho se uloží bod, ve kterém dochází k přetahování. To se používá později v průběhu <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> události upravit překladu rozdílové hodnoty tak, aby her část přepravuje do řádku za místo přetažení.  
  
 A konečně tato metoda vrátí stav zachycení myši. Díky tomu [GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md) objekt ke správě zachytávání po hry na více místech.  
  
 Následující kód ukazuje **UpdateFromMouse** metody.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_UpdateFromMouse](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_updatefrommouse)]  
  
## <a name="processing-manipulations"></a>Zpracování manipulace  
 Po zahájení zpracování <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Started> událost se vyvolá. Obslužná rutina události zastaví nečinnost zpracování, pokud se děje a nastaví *processInertia* příznak `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationStarted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationstarted)]  
  
 Jako hodnoty přidružené ke změně manipulaci s <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Delta> událost se vyvolá. Obslužná rutina pro tuto událost používá rozdílové hodnoty předány argumenty v případě měnit hodnoty pozice a otočení her část.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationdelta)]  
  
 Když jsou odebrány všechny manipulátory (v tomto případě jedné manipulátor), které jsou spojeny s manipulaci s, vyvolá procesoru manipulaci s <xref:System.Windows.Input.Manipulations.ManipulationProcessor2D.Completed> událostí. Obslužné rutiny pro tuto událost začíná nečinnost zpracování tak, že nastavíte počáteční pestrosti nečinný procesor těm, které jsou hlášené argumenty události a nastaví *processInertia* příznak `true`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnManipulationCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_onmanipulationcompleted)]  
  
## <a name="processing-inertia"></a>Zpracování nečinnosti  
 Jako zpracování nečinnost extrapolates nové hodnoty pro angular a lineární pestrosti, souřadnice polohy (překlad) a otočení, <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> událost se vyvolá. Obslužná rutina pro tuto událost používá rozdílové hodnoty předány argumenty v události ke změně pozice a otočení her část.  
  
 Pokud nový souřadnice výsledkem her část překonání hranice zobrazení portů, rychlost zpracování nečinnost je obrácený. To způsobí, že her část kolísají mimo hranice zobrazení portů, která byla zjištěna.  
  
 Nelze změnit vlastnosti <xref:System.Windows.Input.Manipulations.InertiaProcessor2D> objektu během jejího běhu extrapolaci. Proto při stornování rychlosti X nebo Y, obslužná rutina události nejprve zastaví nečinnost voláním <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Complete%2A> metody. Pak přiřadí nové počáteční hodnoty, které mají být aktuální rychlosti hodnoty (přizpůsobené pro chování relaxační) a nastaví *processInertia* příznak `true`.  
  
 Následující kód ukazuje obslužné rutiny události pro <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> událostí.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaDelta](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiadelta)]  
  
 Po dokončení zpracování nečinnost nečinný procesor vyvolá <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Completed> událostí. Nastaví obslužnou rutinu pro tuto událost *processInertia* příznak `false`.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_OnInertiaCompleted](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_oninertiacompleted)]  
  
 Žádná z logiky doposud předložených skutečně způsobí extrapolaci dojít nečinnost. To lze provést v **ProcessInertia** metody. Této metody, které je voláno opakovaně smyčky her aktualizace ( [Game.Update](https://docs.microsoft.com/previous-versions/windows/xna/bb199616%28v%3dxnagamestudio.41%29) metoda) kontroluje, jestli *processInertia* příznak je nastaven na `true`a pokud ano, zavolá <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Process%2A> Metoda. Volání této metody extrapolaci způsobí, že dojde k a vyvolá <xref:System.Windows.Input.Manipulations.InertiaProcessor2D.Delta> událostí.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_ProcessInertia](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_processinertia)]  
  
 Herní část není ve skutečnosti vykreslen až do jednoho z přetížení metody vykreslení je volána. První přetížení této metody je volána opakovaně her draw smyčky ( [Game.Draw](https://docs.microsoft.com/previous-versions/windows/xna/bb196422%28v%3dxnagamestudio.41%29) metoda). Tím zkopírujete her část s aktuální pozici, otočení a faktory měřítka.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_Draw](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_draw)]  
  
## <a name="additional-properties"></a>Další vlastnosti  
 Tři privátní vlastnosti jsou používány **GamePiece** třídy.  
  
1.  **Časové razítko** – získá hodnotu časového razítka používané procesory manipulace a nečinnost.  
  
2.  **X** – získá nebo nastaví souřadnici X her část. Při nastavování, upraví hranice používá pro testování přístupů a umístění pivot zpracování procesoru.  
  
3.  **Y** – získá nebo nastaví souřadnici Y her část. Při nastavování, upraví hranice používá pro testování přístupů a umístění pivot zpracování procesoru.  
  
 [!code-csharp[ManipulationXNA#_GamePiece_PrivateProperties](../../../samples/snippets/csharp/VS_Snippets_Misc/manipulationxna/cs/gamepiece.cs#_gamepiece_privateproperties)]  
  
## <a name="see-also"></a>Viz také  
 [Manipulace a nečinnost](../../../docs/framework/common-client-technologies/manipulations-and-inertia.md)  
 [Použití manipulace a nečinnosti v aplikaci XNA](../../../docs/framework/common-client-technologies/use-manipulations-and-inertia-in-an-xna-application.md)  
 [Vytvoření třídy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
 [Vytvoření třídy Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)

---
title: Porovnání architektury webových formulářů ASP.NET a Blazor
description: Přečtěte si, jak se ASP.NET webové formuláře a Blazor Porovnat architektury.
author: danroth27
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/11/2019
ms.openlocfilehash: 9a8e78338aff53002647a10ed9007296e4682b5a
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267708"
---
# <a name="architecture-comparison-of-aspnet-web-forms-and-no-locblazor"></a>Porovnání architektury webových formulářů ASP.NET a Blazor

I když webové formuláře ASP.NET a Blazor mají mnoho podobných konceptů, existují rozdíly v tom, jak fungují. Tato kapitola prověřuje vnitřní pracovní účely a architektury webových formulářů ASP.NET a Blazor .

## <a name="aspnet-web-forms"></a>ASP.NET – webové formuláře

Rozhraní webových formulářů ASP.NET je založené na architektuře zaměřené na stránky. Každá žádost protokolu HTTP pro umístění v aplikaci je samostatnou stránkou, se kterou ASP.NET odpoví. Když se vyžadují stránky, obsah prohlížeče se nahradí výsledky požadované stránky.

Stránky se skládají z následujících součástí:

- HTML značky
- Kód jazyka C# nebo Visual Basic
- Třída s kódem na pozadí obsahující logiku a funkce zpracování událostí
- Ovládací prvky

Ovládací prvky jsou opakovaně použitelné jednotky webového uživatelského rozhraní, které lze programově umístit a zpracovat na stránce. Stránky se skládají ze souborů, které končí *. aspx* obsahující značky, ovládací prvky a nějaký kód. Třídy kódu na pozadí jsou v souborech se stejným základním názvem a příponou *. aspx.cs* nebo *. aspx. vb* v závislosti na použitém programovacím jazyce. Z prodlení webový server interpretuje obsah souborů *. aspx* a kompiluje je pokaždé, když se změní. Tato opětovná kompilace proběhne i v případě, že je webový server již spuštěn.

Ovládací prvky lze sestavit pomocí značek a doručovat jako uživatelské ovládací prvky. Uživatelský ovládací prvek je odvozen z `UserControl` třídy a má podobnou strukturu jako stránka. Značky pro uživatelské ovládací prvky jsou uloženy v souboru *. ascx* . Doprovodná třída kódu na pozadí se nachází v souboru *. ascx.cs* nebo *. ascx. vb* . Ovládací prvky lze také sestavit zcela pomocí kódu, děděním z `WebControl` nebo `CompositeControl` základní třídy.

Stránky mají také rozsáhlý životní cyklus událostí. Každá stránka vyvolává události pro události inicializace, načítání, PreRender a Unload, ke kterým dochází, když modul runtime ASP.NET spustí kód stránky pro každý požadavek.

Ovládací prvky na stránce se obvykle účtují zpátky na stejnou stránku, která je prezentována ovládacím prvkům, a spolu s nimi přenesou datovou část ze skrytého pole formuláře s názvem `ViewState` . `ViewState`Pole obsahuje informace o stavu ovládacích prvků v době, kdy byly vykresleny a prezentovány na stránce, což umožňuje modulu runtime ASP.NET porovnat a identifikovat změny v obsahu odeslaném na server.

## Blazor

Blazor je rozhraní Web UI na straně klienta podobné jako u front-end rozhraní JavaScript, jako je například úhlové nebo reagující. Blazor zpracovává interakce uživatelů a vykresluje potřebné aktualizace uživatelského rozhraní. Blazor*není* založen na modelu požadavek-odpověď. Interakce s uživatelem jsou zpracovávány jako události, které nejsou v kontextu žádné konkrétní žádosti HTTP.

Blazor aplikace se skládají z jedné nebo více kořenových součástí, které jsou vykresleny na stránce HTML.

![::: No-Loc (Blazor)::: komponenty v HTML](./media/architecture-comparison/blazor-components-in-html.png)

Způsob, jakým uživatel Určuje, kde se mají komponenty vykreslovat a jak se komponenty pak budou hostovat pro interakce s uživatelem, jsou [hostující konkrétní model](hosting-models.md) .

Blazor[komponenty](components.md) jsou třídy .NET, které představují opakovaně použitelná část uživatelského rozhraní. Každá komponenta udržuje svůj vlastní stav a určuje vlastní logiku vykreslování, která může zahrnovat vykreslování dalších komponent. Komponenty určují obslužné rutiny událostí pro konkrétní interakce uživatele, které aktualizují stav součásti.

Poté, co komponenta zpracuje událost, Blazor vykreslí komponentu a udržuje přehled o tom, co se změnilo ve vykresleném výstupu. Komponenty se nevykreslují přímo do model DOM (Document Object Model) (DOM). Místo toho se vykreslí do reprezentace v paměti modelu DOM s názvem a `RenderTree` , aby Blazor mohl sledovat změny. Blazor Porovná nově Vykreslený výstup s předchozím výstupem a vypočte rozdíl uživatelského rozhraní, který pak bude platit pro model DOM.

![::: No-Loc (Blazor)::: DOM – interakce](./media/architecture-comparison/blazor-dom-interaction.png)

Komponenty mohou také ručně označovat, že by měly být vykresleny, pokud se jejich stav mění mimo normální událost uživatelského rozhraní. Blazor používá `SynchronizationContext` k vykonání jediného logického vlákna provádění. Metody životního cyklu komponenty a všechna zpětná volání událostí, která jsou aktivována, Blazor jsou provedena na tomto `SynchronizationContext` .

>[!div class="step-by-step"]
>[Předchozí](introduction.md) 
> [Další](hosting-models.md)

---
title: Řízení stavu
description: Naučte se různé přístupy ke správě stavu ve webových formulářích ASP.NET a Blazor.
author: csharpfritz
ms.author: jefritz
ms.date: 05/15/2020
ms.openlocfilehash: bac2f00330113725f09259ca31bdf857a8769f24
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062337"
---
# <a name="state-management"></a>Řízení stavu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Správa stavu je klíčovým konceptem aplikací webových formulářů, které usnadňují funkce zobrazení stav, stav relace, stav aplikace a zpětné odeslání. Tyto stavové funkce rozhraní pomáhající za účelem skrytí správy stavu požadované pro aplikaci a umožnění vývojářům aplikací soustředit se na poskytování jejich funkcí. Při ASP.NET Core a Blazor byly některé z těchto funkcí přemístěné a některé z nich byly zcela odebrány. Tato kapitola si přečte, jak udržovat stav a doručovat stejné funkce s novými funkcemi v Blazor.

## <a name="request-state-management-with-viewstate"></a>Správa stavu požadavku pomocí vlastnosti ViewState

Při diskusích o správě stavů v aplikaci webových formulářů se vám bude zdát, že mnoho vývojářů bude okamžitě považovat stav ViewState. Ve webových formulářích vlastnost ViewState spravuje stav obsahu mezi požadavky HTTP tím, že do prohlížeče odesílá velký kódovaný blok textu zpátky a zpátky. Pole ViewState by mohlo být zahlceno obsahem ze stránky obsahující mnoho prvků, což může být zvětšení na více megabajtů.

S Blazor serverem aplikace udržuje průběžné připojení k serveru. Stav aplikace nazvaný *okruh*se uchovává v paměti serveru, zatímco připojení je považováno za aktivní. Stav se odstraní jenom v případě, že uživatel přejde pryč z aplikace nebo konkrétní stránky v aplikaci. Všichni členové aktivních komponent jsou k dispozici mezi interakcemi se serverem.

Tato funkce má několik výhod:

- Stav součásti je snadno dostupný a není mezi interakcemi znovu sestaven.
- Stav není přenesen do prohlížeče.

Existují však nevýhody trvalého uchovávání stavu součástí v paměti, které je třeba znát:

- Pokud se server restartuje mezi požadavky, ztratí se stav.
- Řešení vyrovnávání zatížení webového serveru aplikace musí zahrnovat rychlé relace, aby se zajistilo, že všechny požadavky ze stejného prohlížeče vrátí na stejný server. Pokud požadavek přejde na jiný server, stav se ztratí.
- Persistence stavu součásti na serveru může způsobit tlak na paměť na webovém serveru.

Z předchozích důvodů nespoléhejte na to, že pouze stav komponenty se nachází v paměti na serveru. Vaše aplikace by měla také zahrnovat některé záložní úložiště dat pro data mezi požadavky. Některé jednoduché příklady této strategie:

- V aplikaci nákupního košíku trvale zachovejte obsah nových položek přidaných do košíku v záznamu databáze. Pokud dojde ke ztrátě stavu na serveru, můžete ho ze záznamů databáze znovu vytvořit.
- Ve webovém formuláři s více částmi budou uživatelé očekávat, že vaše aplikace bude pamatovat hodnoty mezi jednotlivými požadavky. Zapište data mezi příspěvky vašeho uživatele do úložiště dat, aby je bylo možné načíst a sestavit do konečné struktury odpovědí na formuláři po dokončení formuláře s více částmi.

Další podrobnosti o správě stavu v aplikacích Blazor naleznete v tématu [ASP.NET Core Blazor State Management](/aspnet/core/blazor/state-management).

## <a name="maintain-state-with-session"></a>Udržovat stav s relací

Vývojáři webových formulářů mohou spravovat informace o aktuálně fungujícím uživateli pomocí <xref:Microsoft.AspNetCore.Http.ISession?displayProperty=nameWithType> objektu Dictionary. Je dostatečně snadné přidat objekt s klíčem řetězce do objektu `Session` a tento objekt bude k dispozici později během interakce uživatele s aplikací. Při pokusu o odstranění správy interakce s protokolem HTTP `Session` objekt usnadňuje udržování stavu.

Podpis `Session` objektu .NET Framework není stejný jako `Session` objekt ASP.NET Core. Před rozhodnutím o migraci a používání nové funkce stavu relace zvažte, jestli je [v dokumentaci k nové relaci ASP.NET Core](/dotnet/api/microsoft.aspnetcore.http.isession) .

Relace je dostupná na serveru ASP.NET Core a Blazor, ale nedoporučuje se používat jako vhodným způsobem ukládat data do úložiště dat. Stav relace není funkční ani v případě, že Návštěvníci odmítnou v aplikaci používat soubory cookie protokolu HTTP, protože se týkají ochrany osobních údajů.

Konfigurace pro ASP.NET Core a stav relace je k dispozici v části [relace a Správa stavu v ASP.NET Core článku](/aspnet/core/fundamentals/app-state#session-state).

## <a name="application-state"></a>Stav aplikace

`Application`Objekt v rozhraní Web Forms Framework poskytuje hromadné úložiště mezi požadavky pro interakci s konfigurací a stavem oboru aplikace. Stav aplikace byl ideálním místem pro uložení různých vlastností konfigurace aplikace, na které by se měly odkazovat všechny požadavky bez ohledu na to, jakou uživatel požadavek odeslal. Došlo k problému s `Application` objektem, protože data nebyla na více serverech trvalá. Došlo ke ztrátě stavu objektu aplikace mezi restarty.

Stejně jako u nástroje `Session` doporučujeme, aby se data přesunula do trvalého záložního úložiště, ke kterému by bylo možné přibrat více instancí serveru. Pokud jsou k dispozici Nestálá data, ke kterým byste měli mít přístup přes žádosti a uživatele, můžete ji snadno uložit ve službě s jedním prvkem, která může být vložena do součástí, které tyto informace nebo interakce vyžadují.

Konstrukce objektu pro udržení stavu aplikace a jeho spotřeby by mohla vypadat jako následující implementace:

```csharp
public class MyApplicationState
{
    public int VisitorCounter { get; private set; } = 0;

    public void IncrementCounter() => VisitorCounter += 1;
}
```

```csharp
app.AddSingleton<MyApplicationState>();
```

```razor
@inject MyApplicationState AppState

<label>Total Visitors: @AppState.VisitorCounter</label>
```

`MyApplicationState`Objekt je vytvořen pouze jednou na serveru a hodnota `VisitorCounter` je načtena a výstupem v popisku komponenty. `VisitorCounter`Hodnota by měla být trvalá a načtena ze záložního úložiště dat pro zajištění odolnosti a škálovatelnosti.

## <a name="in-the-browser"></a>V prohlížeči

Data aplikací můžete také uložit na straně klienta na zařízení uživatele, která jsou k dispozici později. Existují dvě funkce prohlížeče, které umožňují trvalá data v různých oborech prohlížeče uživatele:

- `localStorage`– vymezen pro celý prohlížeč uživatele. Pokud je stránka znovu načtena, prohlížeč je zavřen a znovu otevřen nebo je otevřena jiná karta se stejnou adresou URL, a `localStorage` to v prohlížeči.
- `sessionStorage`-vymezeno na aktuální kartu prohlížeče uživatele. Pokud se karta znovu načte, stav přetrvává. Pokud však uživatel otevře jinou kartu pro aplikaci nebo zavře a znovu otevře prohlížeč, dojde ke ztrátě stavu.

Můžete napsat nějaký vlastní kód JavaScriptu pro interakci s těmito funkcemi, nebo můžete použít několik balíčků NuGet, které tuto funkci poskytují. Jedním z těchto balíčků je [Microsoft. AspNetCore. ProtectedBrowserStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.ProtectedBrowserStorage).

Pokyny k použití tohoto balíčku k interakci s `localStorage` a naleznete v `sessionStorage` článku [Správa stavů Blazor](/aspnet/core/blazor/state-management#protected-browser-storage-experimental-package) .

>[!div class="step-by-step"]
>[Předchozí](pages-routing-layouts.md) 
> [Další](forms-validation.md)

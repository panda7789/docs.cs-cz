---
title: Ověřování na straně klienta (ověřování v prezentační vrstvy)
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Ověřování na straně klienta (ověřování v prezentační vrstvy)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 2adce39561dd2b97910155ebed595a2df7785c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>Ověřování na straně klienta (ověřování v prezentační vrstvy)

I v případě, že je zdroj založená modelu domény a nakonec musí mít ověření na úrovni modelu domény, můžete ověření dosud zpracovány na úrovni modelu domény (na straně serveru) i na straně klienta.

Ověřování na straně klienta je velmi užitečný pro uživatele. Ho šetří čas, které by jinak tráví čekání na dobu odezvy na server, který může znovu objevit chyby ověření. V obchodní podmínky dokonce i pár zlomků sekund násobí stokrát každý den přidá do velké množství času, náklady a před. Snadný a okamžitou ověření umožňuje uživatelům vyšší efektivity práce a vytvořit lepší kvalitu vstup a výstup.

Stejně jako v zobrazení modelu a modelu domény se liší, může být podobné ale pro jiný účel ověření modelu zobrazení a ověření modelu domény. Pokud máte obavy o SUCHÝ (nemáte opakujte sami zásada), vezměte v úvahu, v takovém případě může znamenat opakované použití kódu také párování a v podnikové aplikace, které je důležitější nechcete na straně klienta než postupujte podle SUCHÝCH Princip spojte na straně serveru.

I při použití ověřování na straně klienta, si vždy ověřte příkazech nebo vstupní DTOs v serverovém kódu, protože rozhraní API serveru je možný útok. Provádění obou je obvykle nejlepším řešením vzhledem k tomu, že pokud máte klientské aplikace, z hlediska činnosti koncového uživatele je nejvhodnější proaktivní a není povolena, aby uživatel zadal neplatné informace.

Proto v kódu na straně klienta je obvykle ověřit ViewModels. Může také ověřit klienta výstup DTOs nebo příkazy před jejich odesláním do služby.

Implementace ověřování na straně klienta, závisí na jaký druh klientskou aplikaci, kterou vytváříte. Bude jiný, jsou ověřování dat v web webová aplikace MVC s většinou kód v rozhraní .NET, webové aplikace služby Zabezpečené ověřování HESLA s že ověřování probíhá programového v JavaScript nebo TypeScript, nebo mobilní aplikace programového s Xamarinem a C\#.

## <a name="additional-resources"></a>Další zdroje

### <a name="validation-in-xamarin-mobile-apps"></a>Ověření v mobilních aplikacích Xamarin

-   **Ověření vstupní Text a zobrazit chyby**
    [*https://developer.xamarin.com/recipes/ios/standard\_ovládací prvky nebo textu\_pole nebo ověřit\_vstupní /*](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

-   **Zpětné volání pro ověření**
    [*https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/*](https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/)

### <a name="validation-in-aspnet-core-apps"></a>Ověření v aplikacích ASP.NET Core

-   **Rick Anderson. Přidání ověřování**
    [*https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation*](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation)

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>Ověření v SPA webové aplikace (úhlová 2, TypeScript, JavaScript)

-   **ADO Kukic. Úhlová ověřování 2 formuláře** **
    **[*https://scotch.io/tutorials/angular-2-form-validation*](https://scotch.io/tutorials/angular-2-form-validation)

-   **Ověření formuláře**
    [*https://angular.io/docs/ts/latest/cookbook/form-validation.html*](https://angular.io/docs/ts/latest/cookbook/form-validation.html)

-   **Ověření.** Dokumentace uloženy.
    [*https://breeze.github.io/doc-js/validation.html*](https://breeze.github.io/doc-js/validation.html)

V souhrnu jsou to nejdůležitější koncepty namapoval ověření:

-   Entity a agregace by měl vynutit vlastní konzistence a "vždy platný". Agregační kořeny jsou zodpovědní za konzistence více entit v rámci stejné agregace.

-   Pokud si myslíte, že entita musí zadat neplatném stavu, zvažte použití různých objektový model – například pomocí dočasné DTO, dokud nevytvoříte entita konečné domény.

-   Pokud je potřeba vytvořit několik souvisejících objektů, jako je například agregace, a jsou pouze platné po všechny z nich byly vytvořeny, zvažte použití vzoru objekt pro vytváření.

-   Ověřování rozhraní jsou nejvhodnější konkrétní vrstvy, jako je například prezentační vrstvy nebo vrstvě služba nebo aplikace, ale obvykle není v vrstva modelu domény, protože by musela být silné závislý na představuje rozhraní infrastruktury.

-   S redundantní ověřování na straně klienta je vhodný, ve většině případů, protože aplikace může být aktivní.


>[!div class="step-by-step"]
[Předchozí] (domény modelu layer-validations.md) [Další] (domain události návrhu implementation.md)

---
title: Ověřování na straně klienta (ověřování v prezentačních vrstvách)
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Prozkoumejte klíčové koncepty ověřování na straně klienta.
ms.date: 10/08/2018
ms.openlocfilehash: 4e72dcafafc3144a75afe1fd23a4a779f5667459
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295995"
---
# <a name="client-side-validation-validation-in-the-presentation-layers"></a>Ověřování na straně klienta (ověřování v prezentačních vrstvách)

I když je zdrojem pravdy model domény a nakonec musíte mít ověření na úrovni doménového modelu, může se ověřování stále zpracovávat na úrovni doménového modelu (na straně serveru) i v uživatelském rozhraní (na straně klienta).

Ověřování na straně klienta je pro uživatele vynikajícím pohodlím. Šetří čas, který by jinak stráví čekáním na zpoždění odezvy na server, který může vracet chyby ověřování. V obchodních termínech, dokonce i pár sekund vynásobených stovkami časů, se každý den přidává až do hodně času, nákladů a frustrace. Jednoduché a okamžité ověření umožňuje uživatelům pracovat efektivněji a vytvářet lepší kvalitu vstupu a výstupu.

Stejně jako model zobrazení a doménový model se liší, zobrazení ověření modelu a ověřování modelu domény může být podobné, ale slouží k jinému účelu. Pokud máte obavy o vysušení (princip "Neopakuj se" principu), zvažte, že v tomto případě opětovného použití kódu může také znamenat propojení a v podnikových aplikacích je důležitější, aby nemohlo být spojen se serverem na straně klienta, než aby následoval za SUCHÝm principem.

I když používáte ověřování na straně klienta, měli byste vždy ověřit příkazy nebo vstupní DTO v kódu serveru, protože rozhraní API serveru představují možný vektor útoku. Většinou je nejlepší tip, protože pokud máte klientskou aplikaci, z perspektivy uživatelského prostředí je nejlepší být aktivní a neumožníte uživateli zadat neplatné informace.

Proto v kódu na straně klienta, který obvykle ověřujete ViewModels. Před odesláním do služeb můžete také ověřit výstupní DTO nebo příkazy klienta.

Implementace ověřování na straně klienta závisí na typu klientské aplikace, kterou vytváříte. Bude se lišit v případě, že ověřujete data ve webové aplikaci webové MVC s většinou kódu v rozhraní .NET, Webová aplikace SPA s tímto ověřováním je kódována v JavaScriptu nebo TypeScript nebo mobilní aplikace kódované pomocí Xamarin a C#.

## <a name="additional-resources"></a>Další materiály a zdroje informací

### <a name="validation-in-xamarin-mobile-apps"></a>Ověřování v mobilních aplikacích Xamarin

- **Ověřit zadání textu a zobrazit chyby** \
  [https://developer.xamarin.com/recipes/ios/standard\_controls/text\_field/validate\_input/](https://developer.xamarin.com/recipes/ios/standard_controls/text_field/validate_input/)

-  \ **zpětného volání ověřování**
  <https://developer.xamarin.com/samples/xamarin-forms/XAML/ValidationCallback/>

### <a name="validation-in-aspnet-core-apps"></a>Ověřování v ASP.NET Corech aplikacích

- **Rick Anderson. Přidávání \ ověřování**
  <https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/validation>

### <a name="validation-in-spa-web-apps-angular-2-typescript-javascript"></a>Ověřování v ZABEZPEČENých webových aplikacích (úhlové 2, TypeScript, JavaScript)

- **ADO KuKic. Úhlové 2 \ ověřování formuláře**
  <https://scotch.io/tutorials/angular-2-form-validation>

-  \ **ověření formuláře**
  <https://angular.io/guide/form-validation>

- **Export.** Dokumentaci k Breeze. \
  <https://breeze.github.io/doc-js/validation.html>

V souhrnu se jedná o nejdůležitější pojmy týkající se ověřování:

- Entity a agregace by měly vymáhat svou vlastní konzistenci a být "vždy platné". Agregované kořeny jsou zodpovědné za konzistenci více entit v rámci stejné agregace.

- Pokud se domníváte, že entita potřebuje zadat neplatný stav, zvažte použití jiného objektového modelu – například pomocí dočasného DTO, dokud nevytvoříte konečnou entitu domény.

- Pokud potřebujete vytvořit několik souvisejících objektů, například agregaci a jsou platné pouze po vytvoření všech z nich, zvažte použití modelu továrny.

- Ve většině případů je vhodné, aby bylo redundantní ověřování na straně klienta dobré, protože aplikace může být aktivní.

>[!div class="step-by-step"]
>[Předchozí](domain-model-layer-validations.md)
>[Další](domain-events-design-implementation.md)

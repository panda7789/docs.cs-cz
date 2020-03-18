---
title: Nejnovější změny a knihovny .NET
description: Doporučení osvědčených postupů pro navigaci nejnovější změny při vytváření knihoven .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 2cbd9e0a818b52aede6c9b1f60fdf52dcbd7b96f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400419"
---
# <a name="breaking-changes"></a>Změny způsobující chyby

Je důležité, aby knihovna .NET nalezla rovnováhu mezi stabilitou pro stávající uživatele a inovacemi do budoucna. Autoři knihovny se přiklánějí k refaktoringu a přehodnocení kódu, dokud není dokonalý, ale porušení stávajících uživatelů má negativní dopad, zejména pro knihovny nižší úrovně.

## <a name="project-types-and-breaking-changes"></a>Typy projektů a narušující změny

Způsob použití knihovny komunitou .NET změní vliv narušujících změn na vývojáře koncových uživatelů.

- **Knihovny nízké a střední úrovně,** jako je serializátor, analyzátor HTML, mapovač databázových objektů a relačních mapovačů nebo webový rámec, jsou nejvíce ovlivněny nejnovějšími změnami.

  Balíčky stavebních bloků používají vývojáři koncových uživatelů k vytváření aplikací a další knihovny jako závislosti NuGet. Například vytváříte aplikaci a používáte klienta s otevřeným zdrojovým kódem k volání webové služby. Narušující aktualizace závislosti, kterou klient používá, není něco, co můžete opravit. Je to open-source klient, který je třeba změnit a nemáte nad ním žádnou kontrolu. Musíte najít kompatibilní verze knihoven nebo odeslat opravu do klientské knihovny a čekat na novou verzi. Nejhorší situace je, pokud chcete použít dvě knihovny, které závisí na vzájemně nekompatibilní verze třetí knihovny.

- **Knihovny na vysoké úrovni,** jako je sada ovládacích prvků uživatelského rozhraní, jsou méně citlivé na narušující změny.

  Knihovny vysoké úrovně jsou přímo odkazovány v aplikaci koncového uživatele. Pokud dojde k narušující změny, vývojář může zvolit aktualizaci na nejnovější verzi nebo můžete upravit jejich aplikace pro práci s narušující změny.

✔️ přemýšlejte o tom, jak bude vaše knihovna použita. Jaký vliv budou mít změny na aplikace a knihovny, které je používají?

✔️ při vývoji nízkoúrovňové knihovny .NET minimalizují narušující změny.

✔️ zvážit publikování hlavní přepsání knihovny jako nový balíček NuGet.

## <a name="types-of-breaking-changes"></a>Typy přerušovatých změn

Nejnovější změny spadají do různých kategorií a nemají stejný vliv.

### <a name="source-breaking-change"></a>Změna rozdělení zdroje

Změna přerušení zdroje nemá vliv na spuštění programu, ale způsobí chyby kompilace při příštím překompilování aplikace. Například nové přetížení může vytvořit nejednoznačnost v volání metody, které byly jednoznačné dříve nebo přejmenovaný parametr zlomí volající, kteří používají pojmenované parametry.

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

Vzhledem k tomu, že změna rozdělení zdroje je škodlivá pouze v případě, že vývojáři překompilují své aplikace, je to nejméně rušivá změna. Vývojáři mohou snadno opravit svůj vlastní poškozený zdrojový kód.

### <a name="behavior-breaking-change"></a>Změna narušující chování

Změny chování jsou nejčastějším typem narušující změny: téměř každá změna v chování může někoho zlomit. Změny v knihovně, jako jsou podpisy metod, výjimky vyvržené nebo vstupní nebo výstupní datové formáty, mohou negativně ovlivnit spotřebitele knihovny. I oprava chyby může být kvalifikována jako narušující změna, pokud se uživatelé spoléhali na dříve přerušené chování.

Přidání funkcí a zlepšení špatnéchování je dobrá věc, ale bez péče to může dělat to velmi těžké pro stávající uživatele k upgradu. Jedním z přístupů, který vývojářům pomáhá vypořádat se se změnami narušujícím chování, je skrýt je za nastavení. Nastavení umožňují vývojářům aktualizovat na nejnovější verzi knihovny a zároveň se rozhodnout, že se přihlásí nebo odhlásí z nejnovějších změn. Tato strategie umožňuje vývojářům zůstat aktuální a zároveň umožňuje jejich náročné kód přizpůsobit v průběhu času.

Například ASP.NET Core MVC má koncept [verze kompatibility,](/aspnet/core/mvc/compatibility-version) která upravuje funkce `MvcOptions`povolené a zakázané na .

✔️ ZVAŽTe ponechání nových funkcí ve výchozím nastavení vypnuté, pokud ovlivňují stávající uživatele, a nechte vývojáře, aby se k této funkci přihlásili pomocí nastavení.

### <a name="binary-breaking-change"></a>Binární změna porušení

Binární narušující změna se stane, když změníte veřejné rozhraní API knihovny, takže sestavení zkompilovaná proti starší verze knihovny již nejsou moci volat rozhraní API. Například změna podpisu metody přidáním nového parametru způsobí, že sestavení zkompilovaná <xref:System.MissingMethodException>proti starší verzi knihovny vyvolá .

Binární změna rozdělení může také přerušit **celé sestavení**. Přejmenování sestavení `AssemblyName` pomocí změní identitu sestavení, stejně jako přidání, odebrání nebo změna silného pojmenovávacího klíče sestavení. Změna identity sestavení přeruší veškerý zkompilovaný kód, který jej používá.

❌NEMĚŇTE název sestavení.

❌NEPŘIdávejte, neodebírejte ani neměňte silný pojmenovávacím klíčem.

✔️ zvážit použití abstraktní základní třídy namísto rozhraní.

> Přidání cokoli v rozhraní způsobí, že existující typy, které implementují k selhání. Abstraktní základní třída umožňuje přidat výchozí virtuální implementaci.

✔️ ZVAŽTe <xref:System.ObsoleteAttribute> umístění na typy a členy, které chcete odebrat. Atribut by měl mít pokyny pro aktualizaci kódu, aby již nepoužíval zastaralé rozhraní API.

> Kód, který volá typy <xref:System.ObsoleteAttribute> a metody s bude generovat upozornění sestavení se zprávou zadanou atributu. Upozornění poskytují lidem, kteří používají zastaralé rozhraní API povrchčas k migraci tak, že při odebrání zastaralé rozhraní API, většina z nich již používat.

```csharp
public class Document
{
    [Obsolete("LoadDocument(string) is obsolete. Use LoadDocument(Uri) instead.")]
    public static Document LoadDocument(string uri)
    {
        return LoadDocument(new Uri(uri));
    }

    public static Document LoadDocument(Uri uri)
    {
        // Load the document
    }
}
```

✔️ zvažte zachování typů <xref:System.ObsoleteAttribute> a metod s neomezeně dlouho v knihovnách nízké a střední úrovně.

> Odebrání api je binární narušující změna. Vzhledem k zachování zastaralých typů a metod, pokud jejich údržba je nízká cena a nepřidává mnoho technických dluhů do vaší knihovny. Není odebrání typů a metod může pomoci vyhnout se nejhorší scénáře uvedené výše.

## <a name="see-also"></a>Viz také

- [Důležité informace o verzi a aktualizaci pro vývojáře jazyka C#](../../csharp/whats-new/version-update-considerations.md)
- [Definitivní průvodce změny rozhraní API-lámání v .NET](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [Pravidla pro porušení pravidel změn rozhraní .NET](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[Předchozí](versioning.md)

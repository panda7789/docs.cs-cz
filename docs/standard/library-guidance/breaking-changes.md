---
title: Přerušující změny a knihovny .NET
description: Doporučení osvědčených postupů pro navigaci při zásadních změnách při vytváření knihoven .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 8536662ae1cd9733efbcc0c6526bd69d34a13177
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740980"
---
# <a name="breaking-changes"></a>Změny způsobující chyby

Je důležité, aby knihovna .NET vyhledala rovnováhu mezi stabilitou stávajících uživatelů a inovací pro budoucnost. Autoři knihoven se zabývat refaktoringem a přemýšlení kódu, dokud nebudou dokonalé, ale rozdělení stávajících uživatelů má negativní dopad, zejména pro knihovny nízké úrovně.

## <a name="project-types-and-breaking-changes"></a>Typy projektů a průlomové změny

Způsob, jakým komunita rozhraní .NET používá knihovnu, mění vliv na zásadní změny pro vývojáře koncových uživatelů.

- **Knihovny nízké úrovně a střední úrovně** , jako je serializátor, analyzátor HTML, databázový objekt – relační Mapovač nebo webové rozhraní, jsou ovlivněny zásadními změnami.

  Stavební balíčky jsou používány vývojáři koncových uživatelů k vytváření aplikací a dalších knihoven jako závislostí NuGet. Například vytváříte aplikaci a používáte Open sourceho klienta pro volání webové služby. Zásadní aktualizace závislosti, kterou klient používá, není něco, co můžete opravit. Je to open source klient, který je třeba změnit a nemáte nad ním žádnou kontrolu. Je nutné najít kompatibilní verze knihoven nebo odeslat opravu klientské knihovně a počkat na novou verzi. Nejhorším případem je, že chcete použít dvě knihovny, které závisejí na vzájemně nekompatibilní verzi třetí knihovny.

- **Knihovny vysoké úrovně** , jako je sada ovládacích prvků uživatelského rozhraní, jsou méně citlivé na přerušující změny.

  Knihovny vysoké úrovně jsou přímo odkazovány v aplikaci koncového uživatele. V případě, že dojde k zásadním změnám, může vývojář zvolit aktualizaci na nejnovější verzi nebo může upravit svou aplikaci tak, aby fungovala s průlomovou změnou.

**✔️** se zamyslete nad tím, jak se vaše knihovna bude používat. Jaký vliv budou tyto změny u aplikací a knihoven, které ji používají?

Při vývoji knihovny .NET nízké úrovně je **✔️** minimalizovat zásadní změny.

**✔️ zvažte** publikování většího přepsání knihovny jako nového balíčku NuGet.

## <a name="types-of-breaking-changes"></a>Typy přerušujících změn

Zásadní změny spadají do různých kategorií a nejsou stejně ovlivněny.

### <a name="source-breaking-change"></a>Změna konce zdroje

Zásadní změna zdroje neovlivní spuštění programu, ale způsobí chyby při kompilaci při příštím kompilování aplikace. Například nové přetížení může vytvořit nejednoznačnost v voláních metody, které byly dříve dvojznačné, nebo přejmenovaný parametr způsobí přerušení volajících, které používají pojmenované parametry.

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

Vzhledem k tomu, že se změna zdrojového kódu neškodí jenom v případě, že vývojáři znovu zkompiluje své aplikace, je to nejmenší přerušení při změně. Vývojáři můžou snadno opravit svůj vlastní poškozený zdrojový kód.

### <a name="behavior-breaking-change"></a>Změna narušení chování

Změny chování jsou nejběžnějším typem zásadní změny: téměř jakákoli změna v chování může poškodit někoho. Změny v knihovně, jako jsou signatury metod, vyvolané výjimky nebo vstupní nebo výstupní datové formáty, by mohly mít negativní vliv na uživatele knihovny. I Oprava chyby se může kvalifikovat jako zásadní změna, pokud se uživatelé spoléhali na dříve přerušené chování.

Přidání funkcí a vylepšení špatného chování je vhodné, ale bez péče může být pro stávající uživatele velmi obtížné provést upgrade. Jedním ze způsobů, jak přispět vývojářům v práci s zásadními změnami chování, je skrýt ho za nastavením. Nastavení umožní vývojářům aktualizace na nejnovější verzi vaší knihovny současně se zvolením možnosti výslovný souhlas nebo odhlášení nedostatku změn. Tato strategie umožňuje vývojářům zůstat v aktuálním stavu, zatímco umožní přizpůsobovat jejich využívání kódu v průběhu času.

ASP.NET Core MVC má například koncept [verze kompatibility](/aspnet/core/mvc/compatibility-version) , který upravuje Funkce povolené a zakázané v `MvcOptions`.

**✔️ zvažte** , že se ve výchozím nastavení vypnou nové funkce, pokud mají vliv na existující uživatele a umožní vývojářům, aby se k této funkci přihlásili pomocí nastavení.

### <a name="binary-breaking-change"></a>Změna binárního poškození

K binárnímu poškození dojde, když změníte veřejné rozhraní API vaší knihovny, takže sestavení kompilována proti starším verzím knihovny již nebudou schopna volat rozhraní API. Například změna signatury metody přidáním nového parametru způsobí, že sestavení zkompilované na starší verzi knihovny vyvolají <xref:System.MissingMethodException>.

Binární zásadní změna může také poškodit **celé sestavení**. Přejmenováním sestavení pomocí `AssemblyName` dojde ke změně identity sestavení, protože se přidá, odebere nebo změní silný klíč pojmenování sestavení. Změna identity sestavení způsobí přerušení veškerého zkompilovaného kódu, který ho používá.

**❌** neměňte název sestavení.

**❌** Nepřidávat, odebírat ani měnit silný názvový klíč.

**✔️ zvažte** použití abstraktních základních tříd namísto rozhraní.

> Přidání cokoli do rozhraní způsobí, že existující typy, které ji implementují, selžou. Abstraktní základní třída umožňuje přidat výchozí virtuální implementaci.

**✔️ zvažte** umístění <xref:System.ObsoleteAttribute> na typy a členy, které chcete odebrat. Atribut by měl obsahovat pokyny pro aktualizaci kódu, aby již nepoužíval zastaralé rozhraní API.

> Kód, který volá typy a metody s <xref:System.ObsoleteAttribute>, vygeneruje upozornění sestavení se zprávou poskytnutou atributu. Upozornění dávají uživatelům, kteří používají zastaralý čas na ploše rozhraní API k migraci, takže po odebrání zastaralého rozhraní API už ho nepoužívají.

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

**✔️** zajistěte, aby byly typy a metody s <xref:System.ObsoleteAttribute> po dobu neurčitou v knihovnách nízké úrovně a střední úrovně.

> Odebrání rozhraní API je binární zásadní změna. Vzhledem k tomu, že udržování zastaralých typů a metod, pokud je zachování nízkých nákladů, nepřidává do knihovny velké množství technického dluhu. Neodebrání typů a metod může přispět k tomu, abyste se vyhnuli nejhorším scénářům uvedeným výše.

## <a name="see-also"></a>Viz také:

- [Požadavky na verzi a aktualizace C# pro vývojáře](../../csharp/whats-new/version-update-considerations.md)
- [Konečný průvodce pro změny v .NET v rozhraní API](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [Rozhraní .NET – pravidla změny](https://github.com/dotnet/runtime/blob/master/docs/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[Předchozí](versioning.md)

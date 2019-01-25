---
title: Zásadní změny a knihoven .NET
description: Doporučení osvědčených postupů pro navigaci rozbíjející změny v při vytváření knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: a5cfd2dfb544b2e47a87bd0939990ae73e5eda9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564221"
---
# <a name="breaking-changes"></a>Změny způsobující chyby

Je důležité pro knihovnu .NET najít rovnováhu mezi stabilitu pro stávající uživatele a inovace v budoucnosti. Další knihovny autoři Refaktoring a jiný pohled kód, dokud je ideálním řešením, ale vaše stávající uživatele dopadem na dřívější kód má negativní dopad, zejména pro knihovny nízké úrovně.

## <a name="project-types-and-breaking-changes"></a>Typy projektů a nejnovější změny

Použití knihovny .NET komunitou změní účinek rozbíjející změny v vývojáři představující koncové uživatele.

* **Nízká a střední úrovně knihovny** jako serializátor, analyzátor HTML, objektově relační Mapovač databáze nebo webové rozhraní jsou nejvíce ovlivněné rozbíjející změny.

  Balíčky stavebních bloků se používají vývojáři představující koncové uživatele k vytváření aplikací a dalších knihoven jako závislostí NuGet. Například vytváříte aplikaci a pomocí open source klientské volání webové služby. Nejnovější aktualizace na závislost, kterou klient používá není něco, co můžete opravit. Je open source klientské, kterou je potřeba změnit a nemáte žádnou kontrolu nad ním. Budete muset najít kompatibilní verze knihoven nebo odeslat oprava klientské knihovny a počkat na novou verzi. Nejhorším situace je, pokud budete chtít používat dva knihovny, které jsou závislé na vzájemně nekompatibilní verze knihovny třetí.

* **Základní knihovny** jako sada uživatelského rozhraní jsou méně citlivé na rozbíjející změny v ovládacích prvcích.

  Základní knihovny je odkazováno přímo v aplikaci koncového uživatele. Pokud dojde k rozbíjející změny, Vývojář můžete aktualizovat na nejnovější verzi, nebo můžete upravit své aplikace pro spolupráci s narušující změně.

**PROVEĎTE ✔️** přemýšlení o použití knihovny. Jaký vliv budou změny způsobující chyby mít na aplikací a knihoven, které ji používají?

**PROVEĎTE ✔️** minimalizovat změny způsobující chyby při vývoji nízké úrovně knihovny .NET.

**✔️ ZVAŽTE** publikování hlavní přepsání knihovny jako nový balíček NuGet.

## <a name="types-of-breaking-changes"></a>Typy změny způsobující chyby

Zásadní změny se dělí do různých kategorií a nejsou rovnoměrně dopad.

### <a name="source-breaking-change"></a>Rozbíjející změny zdroje

Zdroj narušující změna nemá vliv na provádění programu, ale způsobí chyby při kompilaci, které se je znovu zkompilovat aplikaci. Například nová přetížení, můžete vytvořit nejednoznačnost volání metod, které byly dříve jednoznačný nebo přejmenováno parametr přeruší volajícím, které používají pojmenované parametry.

```csharp
public class Task
{
    // Adding a type called Task could conflict with System.Threading.Tasks.Task at compilation
}
```

Protože zdroji narušující změna je škodlivých pouze když vývojáři znovu zkompilovat svých aplikací, je nejméně rušivé narušující změně. Vývojáři můžete snadno vyřešit vlastní přerušeno zdrojový kód.

### <a name="behavior-breaking-change"></a>Rozbíjející změny chování

Změny chování jsou nejběžnějším typem rozbíjející změny: téměř všechny změny v chování, které by mohly narušit někdo. Změny do knihovny, jako jsou podpisy metod výjimky vyvolána nebo vstupní nebo výstupní formáty dat, může všechny mít negativní vliv na zákazníky knihovny. I oprava chyby kvalifikovat jako rozbíjející změny, pokud uživatelé spoléhali na dříve nefunkční chování.

Přidání funkcí a vylepšení chybné chování je dobrá věc, ale bez péče o to může být velmi obtížné pro stávající uživatele k upgradu. Jedním z přístupů k pomáhá vývojářům řešit rozbíjející změny v chování je skrýt za nastavení. Nastavení umožňují vývojářům aktualizovat na nejnovější verzi knihovny, zatímco ve stejnou dobu, zvolíte-li vyjádřit výslovný souhlas nebo vyjádřit výslovný nesouhlas rozbíjející změny. Tato strategie umožňuje vývojářům dění přičemž umožníte jejich časově náročný kód upravit v čase.

Například technologie ASP.NET Core MVC má koncept [verze kompatibility](/aspnet/core/mvc/compatibility-version) aplikací, které mění funkcí aktivovaných a deaktivovaných na `MvcOptions`.

**✔️ ZVAŽTE** opuštění nové funkce ve výchozím nastavení, dojde k jejich vliv na stávající uživatele a umožňuje vývojářům vyjádřit výslovný souhlas s funkcí s nastavením.

### <a name="binary-breaking-change"></a>Binární zásadní změna

Zásadní změna binární soubor se stane, když změníte veřejné rozhraní API knihovny, tak sestavení zkompilována proti starší verze knihovny není nadále možné volat rozhraní API. Například Změna signatury metody tak, že přidáte nový parametr způsobí, že sestavení, proti starší verzi knihovny vyvolávat <xref:System.MissingMethodException>.

Zásadní změna binární soubor může také dojít k narušení **celé sestavení**. Přejmenování sestavení `AssemblyName` změní identitu sestavení, jako se přidání, odebrání nebo změna silný klíč názvů sestavení. Změna identity sestavení budou přerušeny všechny zkompilovaný kód, který se používá.

**❌ NEPODPORUJÍ** změnit název sestavení.

**❌ NEPODPORUJÍ** přidat, odebrat nebo změnit silného pojmenování klíče.

**✔️ ZVAŽTE** místo abstraktní základní třídy rozhraní.

> Přidání nic do rozhraní způsobí, že existující typy, které je implementují selhání. Abstraktní základní třída umožňuje přidat výchozí virtuální implementace.

**✔️ ZVAŽTE** uvedení <xref:System.ObsoleteAttribute> na typy a členy, které máte v úmyslu odebrat. Pokyny pro aktualizaci kódu, aby již nebudete používat zastaralé rozhraní API by měl mít atribut.

> Kód, který volá typy a metody s <xref:System.ObsoleteAttribute> zprávou zadaný pro atribut vygeneruje upozornění sestavení. Uživatelé dávající upozornění, kteří používají zastaralé rozhraní API zařízení surface čas k migraci tak, že je odebraný zastaralá rozhraní API, většina jsou jeho použití.

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

**✔️ ZVAŽTE** typy a metody s <xref:System.ObsoleteAttribute> po neomezenou dobu v knihovnách úrovni střední a nízká.

> Odebírá se rozhraní API je binární soubor narušující změna. Vzhledem k tomu udržování zastaralých typů a metod, pokud jejich údržba je s nízkými náklady a velké množství technického dluhu nepřidává do své knihovny. Není odebírání typů a metod může pomoci zabránit nejhorším scénáře uvedených výše.

## <a name="see-also"></a>Viz také:

- [Verze a aktualizace důležité informace pro vývojáře v C#](../../csharp/whats-new/version-update-considerations.md)
- [Úplnou příručku k rozhraní API rozbíjející změny v rozhraní .NET](https://stackoverflow.com/questions/1456785/a-definitive-guide-to-api-breaking-changes-in-net)
- [CoreFX narušující Změna pravidla](https://github.com/dotnet/corefx/blob/master/Documentation/coding-guidelines/breaking-change-rules.md)

>[!div class="step-by-step"]
>[Předchozí](versioning.md)

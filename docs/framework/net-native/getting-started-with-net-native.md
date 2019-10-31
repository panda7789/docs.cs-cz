---
title: Začínáme s .NET Native
ms.date: 03/30/2017
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
ms.openlocfilehash: 1c0c25ddf379c31a9c7b4437d36e7e0cbf1bb2f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128399"
---
# <a name="getting-started-with-net-native"></a>Začínáme s .NET Native

Bez ohledu na to, jestli píšete novou aplikaci pro Windows pro Windows 10 nebo migrujete existující aplikaci pro Windows Store, můžete postupovat podle stejné sady postupů. Pokud chcete vytvořit aplikaci .NET Native, postupujte podle těchto kroků:

1. [Vývoj aplikace Univerzální platforma Windows (UWP), která cílí na Windows 10](#Step1), a testování sestavení ladění vaší aplikace, aby se zajistilo správné fungování.

2. [Zpracovat další reflexi a použití serializace](#Step2).

3. [Nasaďte a otestujte buildy pro vydání vaší aplikace](#Step3).

4. [Ručně vyřešte chybějící metadata](#Step4)a opakujte [Krok 3](#Step3) , dokud nebudou vyřešeny všechny problémy.

> [!NOTE]
> Pokud migrujete stávající aplikaci pro Windows Store do .NET Native, přečtěte si téma [migrace aplikace pro Windows Store do .NET Native](migrating-your-windows-store-app-to-net-native.md).

<a name="Step1"></a>

## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a>Krok 1: vývoj a testování ladicích sestavení vaší aplikace pro UWP

Ať už vyvíjíte novou aplikaci nebo migrujete stávající, provedete stejný postup jako u libovolné aplikace pro Windows.

1. Vytvořte nový projekt UWP v aplikaci Visual Studio pomocí šablony univerzální aplikace pro Windows pro Visual C# nebo Visual Basic. Ve výchozím nastavení jsou všechny aplikace UWP zaměřené na CoreCLR a jejich sestavení vydaných verzí kompilovány pomocí řetězce nástroje .NET Native.

2. Všimněte si, že došlo k některým známým problémům s kompatibilitou mezi kompilováním projektů aplikace UWP pomocí řetězce nástroje .NET Native a bez něj. Další informace najdete v [Průvodci migrací](migrating-your-windows-store-app-to-net-native.md) .

Nyní můžete napsat C# nebo Visual Basic kód proti .NET Native oblasti Surface, která běží v místním systému (nebo v simulátoru).

> [!IMPORTANT]
> Při vývoji aplikace si poznamenejte veškeré použití serializace nebo reflexe v kódu.

Ve výchozím nastavení jsou sestavení ladění kompilována JIT pro povolení rychlého F5 nasazení, zatímco sestavení vydaných verzí jsou kompilována pomocí .NET Native technologie předkompilace. To znamená, že byste měli sestavit a otestovat sestavení pro ladění, aby se zajistilo, že budou fungovat normálně, než je zkompilujete pomocí řetězce nástroje .NET Native.

<a name="Step2"></a>

## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a>Krok 2: zpracování dalších reflexe a serializace využití

Soubor direktiv modulu runtime, default. Rd. XML, je automaticky přidán do projektu při jeho vytváření. Pokud vyvíjíte v C#, najdete je ve složce **vlastností** vašeho projektu. Pokud vyvíjíte v Visual Basic, najdete ho ve složce **můj projekt** projektu.

> [!NOTE]
> Přehled procesu kompilace .NET Native, který poskytuje základní informace o tom, proč je soubor direktiv modulu runtime potřebný, naleznete v tématu [.NET Native a kompilace](net-native-and-compilation.md).

Soubor direktiv modulu runtime slouží k definování metadat, které vaše aplikace potřebuje v době běhu. V některých případech může být vhodná výchozí verze souboru. Nicméně nějaký kód, který závisí na serializaci nebo reflexi, může vyžadovat další položky v souboru direktiv modulu runtime.

**Serializace**

Existují dvě kategorie serializátorů a obojí může vyžadovat další položky v souboru direktiv modulu runtime:

- Serializátory založené na jiných než reflexi. Serializátory nalezené v knihovně tříd .NET Framework, jako jsou <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>a třídy <xref:System.Xml.Serialization.XmlSerializer>, nespoléhají na reflexi. Nicméně vyžadují, aby byl kód generován na základě objektu k serializaci nebo deserializaci.  Další informace naleznete v části "serializace společnosti Microsoft" v tématu [serializace a metadata](serialization-and-metadata.md).

- Serializátory třetích stran. Knihovny serializace třetích stran, nejběžnější je serializátor Newtonsoft JSON, jsou obecně založené na reflexi a vyžadují položky v souboru \*. Rd. XML pro podporu serializace a deserializace objektu. Další informace naleznete v části "serializace třetích stran" v tématu [serializace a metadata](serialization-and-metadata.md).

**Metody, které spoléhají na reflexi**

V některých případech není použití odrazu v kódu zřejmé. Některé běžné rozhraní API nebo programovací vzory nejsou považovány za součást rozhraní API pro reflexi, ale spoléhají na úspěšné provedení reflexe. To zahrnuje následující metody vytváření instancí a metod konstrukce:

- Metoda <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType>

- Metody <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> a <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>

- Metoda <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType>.

Další informace najdete v tématu [rozhraní API, která spoléhají na reflexi](apis-that-rely-on-reflection.md).

> [!NOTE]
> Názvy typů používané v souborech direktiv runtime musí být plně kvalifikované. Například soubor musí místo řetězce zadat "System. String".

<a name="Step3"></a>

## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a>Krok 3: nasazení a testování buildů vydaných verzí vaší aplikace

Po aktualizaci souboru direktiv modulu runtime můžete znovu sestavit a nasadit sestavení vydaných verzí vaší aplikace. .NET Native binární soubory jsou umístěny do podadresáře ILC. out adresáře zadaného v textovém poli **cesta pro výstup sestavení** v dialogovém okně **vlastnosti** projektu, karta **kompilovat** . binární soubory, které nejsou v této složce, nebyly zkompilovány. s .NET Native. Otestujte svou aplikaci důkladně a otestujte všechny scénáře, včetně scénářů selhání, na všech svých cílových platformách.

Pokud vaše aplikace nefunguje správně (zejména v případech, kdy vyvolá výjimky [MissingMetadataException](missingmetadataexception-class-net-native.md) nebo [MissingInteropDataException](missinginteropdataexception-class-net-native.md) za běhu), postupujte podle pokynů v následující části, [Krok 4: Ruční vyřešení chybějících metadata](#Step4). Povolení výjimek první pravděpodobnost vám může usnadnit vyhledání těchto chyb.

Když jste otestovali a laděni sestavení pro ladění vaší aplikace a máte jistotu, že jste vyloučili výjimky [MissingMetadataException](missingmetadataexception-class-net-native.md) a [MissingInteropDataException](missinginteropdataexception-class-net-native.md) , měli byste aplikaci otestovat jako optimalizovanou aplikaci .NET Native. Chcete-li to provést, změňte svou aktivní konfiguraci projektu z **ladění** na **verzi**.

<a name="Step4"></a>

## <a name="step-4-manually-resolve-missing-metadata"></a>Krok 4: Ruční řešení chybějících metadat

Nejběžnějším selháním při .NET Native, že se na ploše nesetkáte, je běhová výjimka [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)nebo [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) . V některých případech se nepřítomnost metadat může projevit jako nepředvídatelné chování nebo dokonce i při selhání aplikace. Tato část popisuje, jak lze tyto výjimky ladit a vyřešit přidáním direktiv do souboru direktiv modulu runtime. Informace o formátu direktiv modulu runtime naleznete v tématu [reference ke konfiguračnímu souboru direktiv modulu runtime (RD. XML)](runtime-directives-rd-xml-configuration-file-reference.md). Po přidání direktiv modulu runtime byste měli aplikaci znovu [nasadit a otestovat](#Step3) a vyřešit všechny nové výjimky [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingInteropDataException](missinginteropdataexception-class-net-native.md)a [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) , dokud nevyskytnou se žádné další výjimky.

> [!TIP]
> Zadejte direktivy modulu runtime na vysoké úrovni, aby byla vaše aplikace odolná vůči změnám kódu.  Doporučujeme přidat direktivy modulu runtime v oboru názvů a na úrovni typu, nikoli na úrovni člena. Počítejte s tím, že může dojít k kompromisům mezi odolností a většími binárními soubory s delší dobou kompilace.

Při řešení chybějící výjimky metadat zvažte tyto problémy:

- Jaká byla aplikace, která se pokouší o provedení před výjimkou?

  - Například se jednalo o datovou vazbu, serializaci nebo deserializaci dat nebo přímo pomocí rozhraní API pro reflexi?

- Jedná se o izolovaný případ, nebo se domníváte, že se setkáte se stejným problémem pro jiné typy?

  - Například výjimka [MissingMetadataException](missingmetadataexception-class-net-native.md) je vyvolána při serializaci typu v objektovém modelu aplikace.  Pokud znáte jiné typy, které budou serializovány, můžete přidat direktivy modulu runtime pro tyto typy (nebo pro jejich obsahující obory názvů v závislosti na tom, jak dobře je kód uspořádán) ve stejnou dobu.

- Můžete přepsat kód, aby nepoužíval reflexi?

  - Například kód používá klíčové slovo `dynamic`, pokud víte, jaký typ chcete očekávat?

  - Volá kód metodu, která závisí na reflexi, pokud je k dispozici nějaká lepší alternativa?

> [!NOTE]
> Další informace o zpracování potíží vycházejících z rozdílů v reflexi a dostupnosti metadat v aplikacích klasické pracovní plochy a .NET Native najdete v tématu [rozhraní API, která spoléhají na reflexi](apis-that-rely-on-reflection.md).

Některé konkrétní příklady zpracování výjimek a dalších problémů, ke kterým dochází při testování vaší aplikace, najdete v těchto tématech:

- [Příklad: Zpracování výjimek při vázání dat](example-handling-exceptions-when-binding-data.md)

- [Příklad: Řešení potíží s dynamickým programováním](example-troubleshooting-dynamic-programming.md)

- [Výjimky za běhu v nativních aplikací .NET](runtime-exceptions-in-net-native-apps.md)

## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Nastavení a konfigurace .NET Native](https://docs.microsoft.com/previous-versions/dn600164(v=vs.110))
- [.NET Native a kompilace](net-native-and-compilation.md)
- [Reflexe a .NET Native](reflection-and-net-native.md)
- [Rozhraní API, která závisí na reflexi](apis-that-rely-on-reflection.md)
- [Serializace a metadata](serialization-and-metadata.md)
- [Migrace aplikace pro Windows Store do .NET Native](migrating-your-windows-store-app-to-net-native.md)

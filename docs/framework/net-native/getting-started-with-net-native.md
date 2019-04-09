---
title: Začínáme s .NET Native
ms.date: 03/30/2017
ms.assetid: fc9e04e8-2d05-4870-8cd6-5bd276814afc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ff4db5216cf984af764176fef636bb586f97c2a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081486"
---
# <a name="getting-started-with-net-native"></a>Začínáme s .NET Native
Ať už vytváříte nové aplikace Windows pro Windows 10 nebo migrujete stávající aplikace pro Windows Store, můžete použít stejnou sadu postupy. Chcete-li vytvořit [!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikace, postupujte podle těchto kroků:  
  
1.  [Vývoj aplikace pro univerzální platformu Windows (UPW), který cílí na Windows 10](#Step1)a testování, ladění sestavení vaší aplikace k zajištění, že bude fungovat správně.  
  
2.  [Zpracování další využívání reflection a serializace](#Step2).  
  
3.  [Nasazení a testování buildy vydaných verzí vaší aplikace](#Step3).  
  
4.  [Ruční vyřešení chybějí metadata](#Step4)a opakujte [kroku 3](#Step3) dokud nebudou vyřešeny všechny problémy.  
  
> [!NOTE]
>  Pokud migrujete stávající aplikace pro Windows Store [!INCLUDE[net_native](../../../includes/net-native-md.md)], nezapomeňte si přečíst [migrace Windows Store aplikace pro .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).  
  
<a name="Step1"></a>   
## <a name="step-1-develop-and-test-debug-builds-of-your-uwp-app"></a>Krok 1: Vyvíjejte a testujte sestavení pro ladění vaší aplikace UPW  
 Ať už vyvíjíte novou aplikaci nebo migraci stávající, opakujte stejný postup jako u všech aplikací pro Windows.  
  
1.  Vytvoření nového projektu pro UPW v sadě Visual Studio pomocí šablony aplikace Universal Windows pro jazyk Visual C# nebo Visual Basic. Ve výchozím nastavení cílit na všechny aplikace UPW CoreCLR a jejich sestavení pro vydání jsou kompilovány pomocí .NET Native řetězec nástroje.  
  
2.  Všimněte si, že existují některé problémy s kompatibilitou mezi kompilace projektů aplikací pro UPW s .NET Native řetězec nástrojů a bez něj. Odkazovat [Průvodce migrací](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md) Další informace.  
  
 Teď můžete psát kód jazyka C# nebo Visual Basic [!INCLUDE[net_native](../../../includes/net-native-md.md)] plocha, který běží v místním systému (nebo v simulátoru).  
  
> [!IMPORTANT]
>  Při vývoji vaší aplikace, mějte na paměti jakékoli použití serializaci nebo reflexi ve vašem kódu.  
  
 Ve výchozím nastavení, sestavení pro ladění byly zkompilovány JIT umožňuje rychlé nasazení F5, zatímco verze sestavení jsou kompilovány pomocí [!INCLUDE[net_native](../../../includes/net-native-md.md)] předkompilační technologie. To znamená, že by měl sestavení a testování ladění sestavení vaší aplikace k zajištění, že fungují normálně před kompilací s .NET Native řetězec nástroje.  
  
<a name="Step2"></a>   
## <a name="step-2-handle-additional-reflection-and-serialization-usage"></a>Krok 2: Zpracování další využívání reflection a serializace  
 Soubor direktiv modulu runtime, Default.rd.xml, je automaticky přidán do projektu po jeho vytvoření. Pokud vyvíjíte v jazyce C#, zjistí ve vašem projektu **vlastnosti** složky. Pokud vyvíjíte v jazyce Visual Basic, zjistí ve vašem projektu **Můj projekt** složky.  
  
> [!NOTE]
>  Získáte přehled o .NET Native proces kompilace, která poskytuje na pozadí na důvod, proč je potřeba soubor direktiv modulu runtime, naleznete v tématu [.NET Native a kompilace](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 Soubor direktiv modulu runtime slouží k definování metadat v době běhu podle potřeb vaší aplikace. V některých případech mohou stačit výchozí verzi souboru. Nějaký kód, který je založen na serializaci nebo reflexi však může vyžadovat další položky v souboru direktiv modulu runtime.  
  
 **Serializace**  
 Existují dvě kategorie serializátory a vyžadují další položky v souboru direktiv modulu runtime:  
  
-   Serializátory na Non reflexi. Nenašel serializátory v knihovně tříd rozhraní .NET Framework, jako <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, a <xref:System.Xml.Serialization.XmlSerializer> třídy, nespoléhejte na reflexi. Ale vyžadují, aby se kód vyvolala založené na objekt, který má být serializován nebo deserializován.  Další informace najdete v části "Microsoft Serializers" v [serializace a Metadata](../../../docs/framework/net-native/serialization-and-metadata.md).  
  
-   Serializátory třetích stran. Knihovny třetích stran serializace, nejběžnější z nich je serializátor Newtonsoft JSON, jsou obecně založenými na reflexi a vyžadují položky *. soubor RD.XML, které pro podporu objekt serializace a deserializace. Další informace najdete v části "Serializátory třetích stran" v [serializace a Metadata](../../../docs/framework/net-native/serialization-and-metadata.md).  
  
 **Metody, které závisí na reflexi**  
 V některých případech není zřejmé využívání reflection v kódu. Některé běžné rozhraní API nebo programovací modely nejsou považované za součást rozhraní API reflexe, ale závisí na reflexi proběhl úspěšně. To zahrnuje následující instance typu a metoda konstrukce metody:  
  
-   <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> – Metoda  
  
-   <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> a <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> metody  
  
-   <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> Metody.  
  
 Další informace najdete v tématu [rozhraní API, závisí na reflexi](../../../docs/framework/net-native/apis-that-rely-on-reflection.md).  
  
> [!NOTE]
>  Názvy typů používaných pro soubory direktivy modulu runtime musí být plně kvalifikovaný. Soubor musíte například zadat "System.String" místo "String".  
  
<a name="Step3"></a>   
## <a name="step-3-deploy-and-test-the-release-builds-of-your-app"></a>Krok 3: Nasazení a testování buildy vydaných verzí vaší aplikace  
 Po aktualizaci souboru direktiv modulu runtime, můžete znovu sestavit a nasadit buildy vydaných verzí vaší aplikace. .NET native binární soubory jsou umístěny v podadresáři ILC.out v adresáři uvedeném na **výstupní cesta sestavení** textového pole projektu **vlastnosti** dialogovém okně **kompilaci**kartu. Binární soubory, které nejsou v této složce nebyla kompilována s .NET Native. Důkladně otestujte vaši aplikaci a testovat všechny scénáře, včetně scénářů selhání, na všech jeho cílové platformy.  
  
 Pokud vaše aplikace nebude fungovat správně (zejména v případech, kdy vyvolá [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) nebo [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) výjimky za běhu), postupujte podle pokynů v následujících části [krok 4: Ruční vyřešení chybějí metadata](#Step4). Povolení výjimkách first-chance vám mohou pomoci najít tyto chyby.  
  
 Pokud jste otestovali a ladit ladění sestavení vaší aplikace a Věříme, že jste odstranili [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) a [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) výjimky, měli byste otestovat aplikace jako optimalizované [!INCLUDE[net_native](../../../includes/net-native-md.md)] aplikace. K tomuto účelu změnit konfiguraci aktivního projektu z **ladění** k **vydání**.  
  
<a name="Step4"></a>   
## <a name="step-4-manually-resolve-missing-metadata"></a>Krok 4: Ruční vyřešení chybějí metadata  
 Nejčastější chyby můžete setkat s [!INCLUDE[net_native](../../../includes/net-native-md.md)] není narazíte na ploše je modul runtime [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), nebo [ MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky. V některých případech neexistence metadat může projevit v nepředvídatelné chování nebo dokonce i chyby aplikace. Tato část popisuje, jak můžete ladit a li tyto výjimky vyřešit přidáním direktivy do souboru direktiv modulu runtime. Informace o formátu direktivy modulu runtime naleznete v tématu [direktivy modulu Runtime (rd.xml) odkaz na soubor konfigurace](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Po přidání direktivy modulu runtime, měli byste [nasazení a testování vaší aplikace](#Step3) znovu a vyřešte všechny nové [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), a [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) výjimky, dokud narazíte na žádné další výjimky.  
  
> [!TIP]
>  Zadejte direktivy modulu runtime na vysoké úrovni aplikace chcete být odolní vůči změny kódu.  Doporučujeme přidat direktivy modulu runtime na úrovni oboru názvů a typ a nikoli na úrovni člena. Všimněte si, že může být kompromis mezi větší binární soubory s delší dobu potřebnou ke kompilaci a odolnosti.  
  
 Při adresování chybějící výjimka metadata, zvažte tyto problémy:  
  
-   Co aplikace snažil provést před výjimkou?  
  
    -   Například bylo datové vazby, serializaci nebo deserializaci dat nebo přímo pomocí operace reflection API?  
  
-   Je to izolované případ, nebo máte pocit, že dojde k stejný problém u jiných typů?  
  
    -   Například [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) při serializaci typ v objektovém modelu aplikace, je vyvolána výjimka.  Pokud znáte jiné typy, které bude serializována, můžete přidat direktivy modulu runtime pro typy (nebo pro obory názvů, v závislosti na tom, jak dobře je kód uspořádané) ve stejnou dobu.  
  
-   Můžete tak nepoužívá reflexi revize kódu?  
  
    -   Například používá kód `dynamic` – klíčové slovo, když víte, jaký typ očekávat?  
  
    -   Kód volá metodu, která závisí na reflexi, pokud některé lepší alternativou je k dispozici?  
  
> [!NOTE]
>  Další informace o zpracování problémy, které vyplývají z rozdíly v reflexi a dostupnost metadat v aplikacích klasické pracovní plochy a [!INCLUDE[net_native](../../../includes/net-native-md.md)], naleznete v tématu [rozhraní API, která závisí na reflexi](../../../docs/framework/net-native/apis-that-rely-on-reflection.md).  
  
 Některé konkrétní příklady zpracování výjimek a další problémy, ke kterým dochází při testování vaší aplikace naleznete v tématu:  
  
-   [Příklad: Zpracování výjimek při vázání dat](../../../docs/framework/net-native/example-handling-exceptions-when-binding-data.md)  
  
-   [Příklad: Řešení potíží s dynamickým programováním](../../../docs/framework/net-native/example-troubleshooting-dynamic-programming.md)  
  
-   [Výjimky za běhu v nativních aplikací .NET](../../../docs/framework/net-native/runtime-exceptions-in-net-native-apps.md)  
  
## <a name="see-also"></a>Viz také:

- [Informace o konfiguračním souboru direktiv modulu runtime (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Nastavení a konfigurace .NET Native](https://docs.microsoft.com/previous-versions/dn600164(v=vs.110))
- [.NET Native a kompilace](../../../docs/framework/net-native/net-native-and-compilation.md)
- [Reflexe a .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)
- [Rozhraní API, která závisí na reflexi](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)
- [Serializace a metadata](../../../docs/framework/net-native/serialization-and-metadata.md)
- [Migrace aplikace pro Windows Store do .NET Native](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)

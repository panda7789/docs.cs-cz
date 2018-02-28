---
title: "Rozhraní .NET zabezpečení analyzátorů - rozhraní .NET"
description: "Další informace o použití analyzátorů zabezpečení rozhraní .NET v rozhraní .NET Framework analyzátorů balíčku můžete najít a řešit rizika zabezpečení"
keywords: "Rozhraní .NET, .NET core"
author: billwagner
ms.author: billwagner
ms.date: 01/25/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.openlocfilehash: 06a387d72d06609182c8894dd874b241a5d7b69c
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2018
---
# <a name="the-net-framework-analyzer"></a>Nástroje rozhraní .NET Framework Analyzer

Nástroje rozhraní .NET Framework Analyzer můžete najít potenciální problémy v kódu aplikace založené na rozhraní .NET Framework. Tento analyzátor vyhledá potenciální problémy a navrhne opravy k nim.

Nástroje analyzer spuštěn v interaktivním režimu v sadě Visual Studio při psaní kódu nebo jako součást položky konfigurace sestavení. Měli byste přidat nástroje analyzer do projektu co nejdříve vývoj. Tím dříve najít všechny potenciální problémy ve vašem kódu, tím snazší jsou opravit. Ale můžete přidat kdykoli v cyklu vývoje. Ho vyhledá všechny problémy s stávající kód a upozorňuje o nové problémy jako zachovat vývoj.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>Instalace a konfigurace nástroje Analyzer rozhraní .NET Framework

Jako balíčku NuGet, na každém projektu, kam chcete, aby se spouštěly musí být nainstalován analyzátorů zabezpečení rozhraní .NET. Pouze jeden vývojář musí je přidejte do projektu. Balíček Analyzátor je závislost projektu a bude spuštěn na počítači každý vývojář, jakmile je aktualizovaný řešení.

Nástroje rozhraní .NET Framework Analyzer doručuje v [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) balíček NuGet. Tento balíček poskytuje jenom analyzátorů specifické pro rozhraní .NET Framework, který obsahuje analyzátory zabezpečení. Ve většině případů je výhodné [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) balíček NuGet. Agregační balíček FxCopAnalyzers obsahuje všechny analyzátory framework součástí balíčku Framework.Analyzers, jakož i analyzátorů následující:
- [Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): poskytuje obecné pokyny a doporučené postupy pro standardní rozhraní API technologie .NET
- [Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): poskytuje analyzátorů konkrétní k rozhraní API .NET Core.
- [Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): poskytuje pokyny pro text zahrnuty jako kód, včetně komentář.

K její instalaci, klikněte pravým tlačítkem na projekt a vyberte "Závislosti spravovat".
V Průzkumníku NuGet, vyhledejte "NetFramework Analyzer", nebo pokud dáváte přednost, "Fx Cop Analyzer". Nejnovější stabilní verze nainstalujte na všechny projekty v řešení.

## <a name="using-the-net-framework-analyzer"></a>Pomocí Analyzéru rozhraní .NET Framework

Po instalaci balíčku NuGet, sestavte řešení. Analyzátoru oznámí jakýchkoliv problémů, které je možné vyhledat ve vašem základu kódu. Tyto problémy jsou hlášeny jako upozornění v okně Seznam chyb Visual Studio, jak je znázorněno na následujícím obrázku:

![problémy hlášené analyzátor framework](./media/framework-analyzers-2.png)

Při psaní kódu zobrazí podtržení vlnovkou pod všechny potenciální problém ve vašem kódu.
Najeďte myší na jakýkoli problém a zobrazit podrobnosti o problému a návrhy pro všechny možné opravu, jak je znázorněno na následujícím obrázku:

![interaktivní sestavy problémy nalezené pomocí analyzátoru framework](./media/framework-analyzers-1.png)

Analyzátory Kontrola kódu ve vašem řešení a poskytují seznam upozornění pro některý z těchto problémů:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typy by neměly rozšířit určité základní typy

Existuje několik typů v rozhraní .NET Framework, které byste měli není odvozen od přímo. 

**Kategorie:** návrhu

**Závažnost:** upozornění

Další informace: [CA:1058: typy by neměly rozšířit určité základní typy](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: Zachytávat výjimky v poškozeném stavu

Chyby (například porušení přístupu), což je v nekonzistentním stavu spuštění nebo usnadnit útočník ohrozit systém může masku zachycení výjimky v poškozeném stavu. Místo toho catch a popisovač další konkrétní nastavit výjimka typu (typů) nebo znovu vyvolání výjimky

**Kategorie:** zabezpečení

**Závažnost:** upozornění

Další informace: [## CA2153: zachytávat výjimky v poškozeném stavu](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implementovat serializační konstruktory

Analyzátoru generuje toto upozornění, když vytvoříte typ, který implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní ale nedefinuje konstruktor požadované serializace. Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla. Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný. Konstruktor serializace má následující podpis:

```csharp
public class MyItemType
{
    // The special constructor is used to deserialize values.
    public MyItemType(SerializationInfo info, StreamingContext context)
    {
        // implementation removed.
    }
}
```

**Kategorie:** využití

**Závažnost:** upozornění

Další informace: [CA2229: implementovat Serializační konstruktory](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Označte všechna neserializovatelná pole

Neserializovatelný typ pole instance je deklarován v serializovatelném typu. Je třeba explicitně označit toto pole se <xref:System.NonSerializedAttribute> opravit toto upozornění.

**Kategorie:** využití

**Závažnost:** upozornění

Další informace: [CA2235: označte všechna neserializovatelná pole](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: Označte typy ISerializable pomocí serializovatelný

Rozpoznala modul common language runtime jako serializable, musí být označen typy pomocí <xref:System.SerializableAttribute> atribut i v případě, že typ používá vlastní serializace rutiny implementací <xref:System.Runtime.Serialization.ISerializable> rozhraní.

**Kategorie:** využití

**Závažnost:** upozornění

Další informace: [CA2237: typy označit ISerializable pomocí serializovatelný](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: Nezabezpečené DTD zpracování v kódu XML

Pokud používáte nezabezpečené <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instance nebo odkaz na externí entity zdroje, analyzátor může přijímat nedůvěryhodná pro vstup a prozrazeny citlivé informace útočníci.  

**Kategorie:** zabezpečení

**Závažnost:** upozornění

Další informace: [A3075: nezabezpečené DTD zpracování v kódu XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)


### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nepoužívejte slabé kryptografické algoritmy

Kryptografické algoritmy snížit časem jako stát pokročilejší útoky. V závislosti na typu a použití této kryptografických algoritmů, další snížení jeho síly kryptografického může útočníkovi umožnit, aby číst zprávy typu enciphered, manipulovat s enciphered zprávy, forge digitální podpisy, manipulovat s hash obsahu, nebo v opačném případě ohrozit zabezpečení jakékoli cryptosystem podle tento algoritmus. Pro šifrování, použít algoritmus standardu AES (AES 256, AES-192 a AES-128 jsou přijatelná) s délkou klíče větší než nebo rovna hodnotě 128 bitů. Pro použití algoritmu hash, použijte funkce algoritmu hash řady SHA-2, jako je například 512 SHA-2, 384 SHA-2 a SHA-2 256.

**Kategorie:** zabezpečení

**Závažnost:** upozornění

Další informace: [CA5350: Nepoužívejte slabé kryptografické algoritmy](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Nepoužívejte porušený kryptografické algoritmy

Útok provedení výpočetně vhodný pro tento algoritmus přerušení existuje. To umožňuje útočníkům rozdělit kryptografických záruky, které je určená k poskytnutí. V závislosti na typu a použití této kryptografických algoritmů to může útočníkovi umožnit, aby enciphered zprávy číst, manipulovat s enciphered zprávy, forge digitální podpisy, manipulovat s hash obsahu nebo jinak ohrozit zabezpečení jakékoli cryptosystem na základě na tento algoritmus. Pro šifrování, použít algoritmus standardu AES (AES 256, AES-192 a AES-128 jsou přijatelná) s délkou klíče větší než nebo rovna hodnotě 128 bitů. Pro použití algoritmu hash, použijte funkce algoritmu hash řady SHA-2, jako je například SHA512, SHA384 nebo SHA256. Pro digitální podpisy použijte RSA s délkou klíče větší než nebo rovna hodnotě 2048 bitů nebo ECDSA s délkou klíče větší než nebo rovna 256 bitů.

**Kategorie:** zabezpečení

**Závažnost:** upozornění

Další informace: [CA5351: Nepoužívejte porušený kryptografické algoritmy](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)



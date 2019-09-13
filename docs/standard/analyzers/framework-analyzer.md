---
title: Analyzátory zabezpečení .NET – .NET
description: Přečtěte si, jak pomocí analyzátorů zabezpečení .NET v balíčku .NET Framework analyzátory najít a vyřešit bezpečnostní rizika.
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: da5e72b96fec35404e7e9ae7930f3430143487d2
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929299"
---
# <a name="the-net-framework-analyzer"></a>Analyzátor .NET Framework

K nalezení potenciálních problémů v kódu aplikace založeném na .NET Framework můžete použít analyzátor .NET Framework. Tento analyzátor vyhledá možné problémy a navrhne jejich opravy.

Analyzátor se spustí interaktivně v aplikaci Visual Studio při psaní kódu nebo jako součást sestavení CI. Analyzátor byste měli přidat do projektu co nejdříve ve vašem vývoji. Dříve najdete případné problémy v kódu, což je snazší opravit. Můžete ho ale kdykoli přidat do vývojového cyklu. Vyhledá všechny problémy s existujícím kódem a upozorní na nové problémy při vývoji.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>Instalace a konfigurace analyzátoru .NET Framework

Analyzátory zabezpečení .NET musí být nainstalované jako balíček NuGet v každém projektu, kde se mají spouštět. Pouze jeden vývojář potřebuje přidat do projektu. Balíček analyzátoru je závislý na projektu a spustí se na každém počítači vývojáře, jakmile bude mít aktualizované řešení.

Analyzátor .NET Framework je dodán v balíčku NuGet [Microsoft. NETFramework. analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) . Tento balíček poskytuje jenom analyzátory, které jsou specifické pro .NET Framework, které zahrnují analyzátory zabezpečení. Ve většině případů budete chtít balíček NuGet [Microsoft. CodeAnalysis. FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) . FxCopAnalyzers agregovaný balíček obsahuje všechny analyzátory rozhraní, které jsou součástí balíčku Framework. Analyzers a také následující analyzátory:

- [Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Poskytuje obecné pokyny a pokyny pro rozhraní API pro .NET Standard.
- [Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Poskytuje analyzátory specifické pro rozhraní API .NET Core.
- [Text. analyzers](https://www.nuget.org/packages/Text.Analyzers): Obsahuje pokyny pro text zahrnutý jako kód, včetně komentářů.

Pokud ho chcete nainstalovat, klikněte pravým tlačítkem na projekt a vyberte spravovat závislosti.
V Průzkumníku NuGet vyhledejte "NetFramework Analyzer", nebo pokud dáváte přednost, "FX VPP Analyzer". Nainstalujte nejnovější stabilní verzi do všech projektů ve vašem řešení.

## <a name="using-the-net-framework-analyzer"></a>Použití analyzátoru .NET Framework

Po instalaci balíčku NuGet si sestavte řešení. Analyzátor ohlásí všechny problémy, které najde ve vašem základu kódu. Problémy jsou hlášeny jako upozornění v okně Visual Studio Seznam chyb, jak je znázorněno na následujícím obrázku:

![problémy hlášené analyzátorem rozhraní Framework](./media/framework-analyzers-2.png)

Při psaní kódu se zobrazí vlnovky pod jakýmkoli potenciálním problémem v kódu.
Najeďte myší na libovolný problém a zobrazí se podrobnosti o problému a návrhy na případné opravy, jak je znázorněno na následujícím obrázku:

![interaktivní sestava problémů zjištěných analyzátorem rozhraní](./media/framework-analyzers-1.png)

Analyzátory prozkoumají kód ve vašem řešení a poskytnou vám seznam upozornění pro některý z těchto problémů:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typy by neměly rozšiřovat určité základní typy

V .NET Framework existuje malý počet typů, které byste neměli odvozovat přímo. 

**Kategorií** Návrh

**Závažnost** Upozornění

Další informace: [CA:1058: Typy by neměly rozkrývat určité základní typy](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: Nezachytit poškozené výjimky stavu

Výsledkem zachycení poškozených výjimek stavu mohou být chyby maskování (například porušení přístupu), což vede k nekonzistentnímu stavu provádění nebo je snazší útočníkům napadnout systém. Místo toho Zachyťte a zpracujte konkrétnější sadu typů výjimek nebo znovu vyvolejte výjimku.

**Kategorií** Zabezpečení

**Závažnost** Upozornění

Další informace: [# # CA2153: Nezachytit poškozené výjimky stavu](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implementujte serializační konstruktory

Analyzátor vygeneruje toto upozornění, když vytvoříte typ, který implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní, ale nedefinuje požadovaný konstruktor serializace. Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla. Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný. Konstruktor serializace má následující signaturu:

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

**Kategorií** Použití

**Závažnost** Upozornění

Další informace: [CA2229: Implementovat konstruktory serializace](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Označte všechna neserializovatelná pole

Neserializovatelný typ pole instance je deklarován v serializovatelném typu. <xref:System.NonSerializedAttribute> Chcete-li opravit toto upozornění, je nutné explicitně označit toto pole pomocí.

**Kategorií** Použití

**Závažnost** Upozornění

Další informace: [CA2235: Označte všechna Neserializovatelný pole](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: Označte typy ISerializable s serializovatelným

Aby je bylo možné rozpoznat modulem CLR (Common Language Runtime) jako serializovatelný, musí být <xref:System.SerializableAttribute> typy označeny pomocí atributu, i když typ používá vlastní rutinu serializace <xref:System.Runtime.Serialization.ISerializable> implementací rozhraní.

**Kategorií** Použití

**Závažnost** Upozornění

Další informace: [CA2237: Označte typy ISerializable s serializovatelným](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: Nezabezpečené zpracování DTD v XML

Pokud používáte nezabezpečené <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instance nebo odkazujete na zdroje externích entit, analyzátor může přijmout nedůvěryhodné vstupní a únik citlivých informací útočníkům.  

**Kategorií** Zabezpečení

**Závažnost** Upozornění

Další informace: [A3075: Nezabezpečené zpracování DTD v XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nepoužívejte slabé kryptografické algoritmy.

Kryptografické algoritmy se v průběhu času degradují, jakmile se útoky stanou pokročilejší. V závislosti na typu a aplikaci tohoto kryptografického algoritmu může další degradace jeho kryptografické síly umožnit útočníkům číst enciphered zprávy, manipulovat s enciphered, zfalšovat digitální podpisy, manipulovat s obsahem s hashy nebo v opačném případě ohrožení všech cryptosystem na základě tohoto algoritmu. Pro šifrování použijte algoritmus AES (AES-256, AES-192 a AES-128 jsou přijatelné) s délkou klíče větší nebo rovnou 128 bitů. V případě hashování použijte funkci hash v rodině SHA-2, například SHA-2 512, SHA-2 384 nebo SHA-2 256.

**Kategorií** Zabezpečení

**Závažnost** Upozornění

Další informace: [CA5350: Nepoužívejte slabé kryptografické algoritmy.](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Nepoužívejte nefunkční kryptografické algoritmy.

Útok, který provádí výpočetně vhodným důvodem pro přerušení tohoto algoritmu, existuje. To umožňuje útočníkům přerušit kryptografické záruky, které je navržena pro poskytování. V závislosti na typu a aplikaci tohoto kryptografického algoritmu může útočníkům umožnit čtení zpráv enciphered, manipulace s enciphered zprávami, zfalšovat digitálních podpisů, manipulace s hash obsahem nebo jiné ohrožení zabezpečení založeného na cryptosystem. u tohoto algoritmu. Pro šifrování použijte algoritmus AES (AES-256, AES-192 a AES-128 jsou přijatelné) s délkou klíče větší nebo rovnou 128 bitů. V případě hashování použijte funkci hash, která je v rodině SHA-2, například SHA512, SHA384 nebo SHA256. U digitálních podpisů použijte RSA s délkou klíče větší nebo rovnou 2048 bitů nebo ECDSA s délkou klíče větší nebo rovnou 256 bitů.

**Kategorií** Zabezpečení

**Závažnost** Upozornění

Další informace: [CA5351: Nepoužívejte nefunkční kryptografické algoritmy.](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)

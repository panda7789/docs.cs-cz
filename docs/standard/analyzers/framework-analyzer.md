---
title: Analyzátory rozhraní .NET Framework - .NET
description: Zjistěte, jak pomocí analyzátorů rozhraní .NET Framework v balíčku analyzátorů rozhraní .NET Framework vyhledat a řešit rizika zabezpečení.
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: dd69671e709549fe0ad0f582e4d09b43f7321df2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155994"
---
# <a name="the-net-framework-analyzer"></a>Analyzátor rozhraní .NET Framework

Analyzátor rozhraní .NET Framework můžete použít k vyhledání potenciálních problémů v kódu aplikace založené na rozhraní .NET Framework. Tento analyzátor vyhledá potenciální problémy a navrhne jejich opravy.

Analyzátor běží interaktivně v sadě Visual Studio při psaní kódu nebo jako součást sestavení CI. Analyzátor byste měli přidat do projektu co nejdříve ve vašem vývoji. Čím dříve najdete potenciální problémy ve vašem kódu, tím snadněji se opravují. Můžete jej však přidat kdykoli ve vývojovém cyklu. Najde všechny problémy s existující kód a varuje před novými problémy, jak budete pokračovat v rozvoji.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>Instalace a konfigurace analyzátoru rozhraní .NET Framework Analyzer

Analyzátory rozhraní .NET Framework musí být nainstalovány jako balíček NuGet v každém projektu, kde je chcete spustit. Do projektu je musí přidat pouze jeden vývojář. Balíček analyzátoru je závislost projektu a bude spuštěn na každém počítači vývojáře, jakmile bude mít aktualizované řešení.

Analyzátor rozhraní .NET Framework je dodáván v balíčku [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) NuGet. Tento balíček obsahuje pouze analyzátory specifické pro rozhraní .NET Framework, který zahrnuje analyzátory zabezpečení. Ve většině případů budete chtít [Balíček NuGet Microsoft.CodeAnalysis.FxCopAnalyzers.](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers)
Agregační balíček FxCopAnalyzers obsahuje všechny rámcové analyzátory obsažené v balíčku Framework.Analyzers, stejně jako následující analyzátory:

- [Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Poskytuje obecné pokyny a pokyny pro rozhraní API standardu .NET
- [Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Poskytuje analyzátory specifické pro rozhraní API .NET Core.
- [Text.Analyzátory](https://www.nuget.org/packages/Text.Analyzers): Poskytuje pokyny pro text zahrnutý jako kód, včetně komentářů.

Chcete-li jej nainstalovat, klikněte pravým tlačítkem myši na projekt a vyberte možnost Spravovat závislosti.
Z NuGet explorer, hledat "NetFramework Analyzer", nebo pokud dáváte přednost, "Fx Cop Analyzer". Nainstalujte nejnovější stabilní verzi ve všech projektech ve vašem řešení.

## <a name="using-the-net-framework-analyzer"></a>Použití analyzátoru rozhraní .NET Framework Analyzer

Po instalaci balíčku NuGet, sestavení řešení. Analyzátor ohlásí všechny problémy, které najde ve vašem základu kódu. Problémy jsou hlášeny jako upozornění v okně Seznam chyb sady Visual Studio, jak je znázorněno na následujícím obrázku:

![problémy hlášené rámcovým analyzátorem](./media/framework-analyzers-2.png)

Při psaní kódu, vidíte vlnovky pod jakýkoli potenciální problém v kódu.
Najeďte na libovolný problém a zobrazí se podrobnosti o problému a návrhy na možnou opravu, jak je znázorněno na následujícím obrázku:

![interaktivní zpráva o problémech zjištěných rámcovým analyzátorem](./media/framework-analyzers-1.png)

Analyzátory zkontroluje kód ve vašem řešení a poskytují vám seznam upozornění pro všechny z těchto problémů:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typy by neměly rozšířit určité základní typy

Existuje malý počet typů v rozhraní .NET Framework, které byste neměli odvodit přímo.

**Kategorie:** Design

**Závažnost:** Upozornění

Další informace: [CA:1058: Typy by neměly rozšiřovat určité základní typy.](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: Nezachytit výjimky poškozeného stavu

Zachycení výjimky poškozeného stavu může maskovat chyby (například narušení přístupu), což má za následek nekonzistentní stav spuštění nebo usnadňuje útočníkům ohrožení systému. Místo toho zachyťte a zpracovat konkrétnější sadu typů výjimek nebo znovu vyvolat výjimku

**Kategorie:** Zabezpečení

**Závažnost:** Upozornění

Další informace: [## CA2153: Nezachytát výjimky poškozeného stavu](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implementovat serializační konstruktory

Analyzátor generuje toto upozornění při vytváření typu, <xref:System.Runtime.Serialization.ISerializable> který implementuje rozhraní, ale nedefinuje požadovaný konstruktor serializace. Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla. Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný. Konstruktor serializace má následující podpis:

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

**Kategorie:** Použití

**Závažnost:** Upozornění

Další informace: [CA2229: Implementace konstruktorů serializace](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Označte všechna neserializovatelná pole

Neserializovatelný typ pole instance je deklarován v serializovatelném typu. Chcete-li toto upozornění <xref:System.NonSerializedAttribute> opravit, je nutné toto pole explicitně označit.

**Kategorie:** Použití

**Závažnost:** Upozornění

Další informace: [CA2235: Označení všech neserializovatelných polí](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: Označit iSerializable typy s serializovatelné

Chcete-li být rozpoznán modulu runtime společného jazyka jako <xref:System.SerializableAttribute> serializovatelný, musí být typy označeny pomocí <xref:System.Runtime.Serialization.ISerializable> atributu i v případě, že typ používá vlastní serializační rutinu implementací rozhraní.

**Kategorie:** Použití

**Závažnost:** Upozornění

Další informace: [CA2237: Označit iSerializable typy s serializovatelný](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: Nezabezpečené zpracování DTD v XML

Pokud použijete <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> nezabezpečené instance nebo odkazujete na zdroje externích entit, analyzátor může přijmout nedůvěryhodný vstup a zpřístupnit citlivé informace útočníkům.  

**Kategorie:** Zabezpečení

**Závažnost:** Upozornění

Další informace: [A3075: Nezabezpečené zpracování DTD v XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nepoužívejte slabé kryptografické algoritmy

Kryptografické algoritmy se časem znehodnocují s tím, jak se útoky stávají pokročilejšími. V závislosti na typu a použití tohoto kryptografického algoritmu může další degradace jeho kryptografické síly umožnit útočníkům číst šifrované zprávy, manipulovat se šifrovanými zprávami, falšovat digitální podpisy, manipulovat s obsahem hash nebo jinak ohrozit jakýkoli kryptosystém založený na tomto algoritmu. Pro šifrování použijte algoritmus AES (AES-256, AES-192 a AES-128 jsou přijatelné) s délkou klíče větší nebo rovnou 128 bitům. Pro zahasování použijte funkci hash v rodině SHA-2, například SHA-2 512, SHA-2 384 nebo SHA-2 256.

**Kategorie:** Zabezpečení

**Závažnost:** Upozornění

Další informace: [CA5350: Nepoužívejte slabé kryptografické algoritmy](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Nepoužívejte nefunkční kryptografické algoritmy

Existuje útok, který je technicky proveditelný k přerušení tohoto algoritmu. To umožňuje útočníkům přerušit kryptografické záruky, které je určen k poskytování. V závislosti na typu a použití tohoto kryptografického algoritmu to může útočníkům umožnit číst šifrované zprávy, manipulovat s šifrovanými zprávami, falšovat digitální podpisy, manipulovat s obsahem hash nebo jinak ohrozit jakýkoli kryptosystém založený na tomto algoritmu. Pro šifrování použijte algoritmus AES (AES-256, AES-192 a AES-128 jsou přijatelné) s délkou klíče větší nebo rovnou 128 bitům. Pro zahasování použijte funkci hash v rodině SHA-2, například SHA512, SHA384 nebo SHA256. Pro digitální podpisy použijte RSA s délkou klíče větší nebo rovnou 2048 bitům nebo ECDSA s délkou klíče větší nebo rovnou 256 bitům.

**Kategorie:** Zabezpečení

**Závažnost:** Upozornění

Další informace: [CA5351: Nepoužívejte nefunkční kryptografické algoritmy](/visualstudio/code-quality/ca5351)

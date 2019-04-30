---
title: Analýzu zabezpečení pro .NET – .NET
description: Další informace o použití analyzátory .NET zabezpečení v rozhraní .NET Framework analyzátory balíčku k vyhledávání a řešení bezpečnostních rizik
author: billwagner
ms.author: wiwagn
ms.date: 01/25/2018
ms.technology: dotnet-standard
ms.openlocfilehash: cbd9bcdb12a423f54aa4ff82d88f07c20023c48f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947295"
---
# <a name="the-net-framework-analyzer"></a>Analyzátor rozhraní .NET Framework

Analyzátor rozhraní .NET Framework můžete použít k vyhledání potenciálních problémů v kódu aplikace založené na rozhraní .NET Framework. Tento analyzátor vyhledá potenciální problémy a navrhne opravy na ně.

Analyzátor spuštěn v interaktivním režimu v sadě Visual Studio vám při psaní kódu nebo jako součást sestavení CI. Měli byste přidat analyzátor do svého projektu co nejdříve při vývoji. Rychleji najít všechny potenciální problémy v kódu, tím snazší opravit. Ale můžete přidat kdykoli v cyklu vývoje. Vyhledá všechny problémy s existující kód a upozorní o nových problémech, jak zachovat vývoj.

## <a name="installing-and-configuring-the-net-framework-analyzer"></a>Instalace a konfigurace analyzátor rozhraní .NET Framework

Analyzátory .NET zabezpečení musí být nainstalován jako balíček NuGet na každý projekt, kam chcete, aby běžela. Pouze jeden vývojář je potřeba je přidat do projektu. Balíček analyzátoru, představuje závislost projektu a bude spuštěn na počítači každý vývojář, jakmile má aktualizované řešení.

Analyzátor rozhraní .NET Framework se doručí do [Microsoft.NetFramework.Analyzers](https://www.nuget.org/packages/Microsoft.NetFramework.Analyzers/) balíček NuGet. Tento balíček poskytuje pouze analyzátory specifické pro rozhraní .NET Framework, která zahrnuje analýzu zabezpečení. Ve většině případů je vhodné [Microsoft.CodeAnalysis.FxCopAnalyzers](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers) balíček NuGet. FxCopAnalyzers agregační balíček obsahuje všechny analyzátory framework součástí balíčku Framework.Analyzers, jakož i analyzátory následující:
- [Microsoft.CodeQuality.Analyzers](https://www.nuget.org/packages/Microsoft.CodeQuality.Analyzers): Obsahuje obecné pokyny a doprovodné materiály k rozhraní API pro .NET Standard
- [Microsoft.NetCore.Analyzers](https://www.nuget.org/packages/Microsoft.NetCore.Analyzers): Poskytuje analyzátory konkrétní rozhraní API pro .NET Core.
- [Text.Analyzers](https://www.nuget.org/packages/Text.Analyzers): Obsahuje pokyny pro text součástí kódu, včetně komentářů.

K jeho instalaci, klikněte pravým tlačítkem na projekt a vyberte "Spravovat závislosti".
Z Průzkumníka NuGet, vyhledejte "NetFramework analyzátor", nebo pokud dáváte přednost, "Fx Cop analyzátor". Nainstalujte nejnovější stabilní verze ve všech projektech v řešení.

## <a name="using-the-net-framework-analyzer"></a>Pomocí Analyzéru rozhraní .NET Framework

Po instalaci balíčku NuGet, sestavte řešení. Analyzátor ohlásí problémů, na které je možné vyhledat ve vašem základu kódu. Problémy označené jako upozornění v okně Seznam chyb Visual Studio, jak je znázorněno na následujícím obrázku:

![problémech ohlášených analyzátor architektury](./media/framework-analyzers-2.png)

Při psaní kódu, uvidíte podtržení vlnovkou pod případné potíže v kódu.
Najeďte myší jakýkoli problém a zobrazit podrobnosti o problému a návrhy pro všechny možné opravu, jak je znázorněno na následujícím obrázku:

![interaktivní sestavy problémů zjištěných aplikací analyzátor architektury](./media/framework-analyzers-1.png)

Analyzátory prozkoumat kód v rámci vašeho řešení a poskytneme vám seznam upozornění pro některý z těchto problémů:

### <a name="ca1058-types-should-not-extend-certain-base-types"></a>CA1058: Typy by neměly rozšiřovat určité základní typy

Existuje několik malých typů v rozhraní .NET Framework, které byste měli není odvozeno od přímo. 

**Kategorie:** Návrh

**Závažnost:** Upozornění

Další informace: [CA:1058: Typy by neměly rozšířit určité základní typy](/visualstudio/code-quality/ca1058-types-should-not-extend-certain-base-types)

### <a name="ca2153-do-not-catch-corrupted-state-exceptions"></a>CA2153: Nezachycujte výjimky v poškozeném stavu

Chyby (například porušení přístupu), což vede k nekonzistentnímu stavu spuštění nebo snadnější útočník napadnout počítač může maskovat zachycení výjimek v poškozeném stavu. Místo toho catch a popisovač další konkrétní sadu výjimek typy nebo opětovné vyvolání výjimky

**Kategorie:** Zabezpečení

**Závažnost:** Upozornění

Další informace: [## CA2153: Nezachycujte výjimky v poškozeném stavu](/visualstudio/code-quality/ca2153-avoid-handling-corrupted-state-exceptions)

### <a name="ca2229-implement-serialization-constructors"></a>CA2229: Implementujte serializační konstruktory

Analyzátor generuje toto upozornění, když vytvoříte typ, který implementuje <xref:System.Runtime.Serialization.ISerializable> rozhraní, ale vyžaduje Serializační konstruktor není definován. Implementací konstruktoru serializace se vyřeší porušení tohoto pravidla. Pro zapečetěnou třídu musí být konstruktor soukromý. V ostatních případech musí být chráněný. Serializační konstruktor má následující podpis:

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

Další informace: [CA2229: Implementovat Serializační konstruktory](/visualstudio/code-quality/ca2229-implement-serialization-constructors)

### <a name="ca2235-mark-all-non-serializable-fields"></a>CA2235: Označte všechna neserializovatelná pole

Neserializovatelný typ pole instance je deklarován v serializovatelném typu. Je třeba explicitně označit toto pole se <xref:System.NonSerializedAttribute> opravit toto upozornění.

**Kategorie:** Použití

**Závažnost:** Upozornění

Další informace: [CA2235: Označte všechna neserializovatelná pole](/visualstudio/code-quality/ca2235-mark-all-non-serializable-fields)

### <a name="ca2237-mark-iserializable-types-with-serializable"></a>CA2237: Označte typy ISerializable pomocí serializovatelného

Chcete-li rozpoznán modulem common language runtime jako serializovatelný, musí být označen pomocí <xref:System.SerializableAttribute> atribut i v případě, že se typ používá vlastní rutinu serializace prostřednictvím implementace <xref:System.Runtime.Serialization.ISerializable> rozhraní.

**Kategorie:** Použití

**Závažnost:** Upozornění

Další informace: [CA2237: Označte typy ISerializable pomocí serializovatelného](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca3075-insecure-dtd-processing-in-xml"></a>CA3075: Nezabezpečené specifikace DTD zpracování ve formátu XML

Pokud používáte nezabezpečené <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> instance nebo odkaz na externí entity zdroje, analyzátor může přijmout nedůvěryhodné vstupní tak zveřejnit citlivé informace, které útočníci.  

**Kategorie:** Zabezpečení

**Závažnost:** Upozornění

Další informace: [A3075: Nezabezpečené specifikace DTD zpracování ve formátu XML](/visualstudio/code-quality/ca2237-mark-iserializable-types-with-serializableattribute)

### <a name="ca5350-do-not-use-weak-cryptographic-algorithms"></a>CA5350: Nepoužívejte slabé kryptografické algoritmy

Postupem času degradovat kryptografické algoritmy, budou další pokročilé útoky. V závislosti na typu a použití tohoto kryptografický algoritmus dále snížení jeho kryptografická můžou útočníkům umožnit, aby číst enciphered zprávy, manipulovat s enciphered zprávy, forge digitální podpisy, manipulovat s hodnotu hash obsahu, nebo v opačném případě ohrozit zabezpečení jakékoli cryptosystem podle algoritmu. Pro šifrování, použijte algoritmus AES (AES-256, AES-192 a AES-128 jsou přijatelná) s délkou klíče větší než nebo rovna hodnotě 128 bitů. Pro vytvoření hodnoty hash, pomocí funkce algoritmu hash řady SHA-2, jako je 512 SHA-2, SHA-2 384 nebo 256 SHA-2.

**Kategorie:** Zabezpečení

**Závažnost:** Upozornění

Další informace: [CA5350: Nepoužívejte slabé kryptografické algoritmy](/visualstudio/code-quality/ca5350-do-not-use-weak-cryptographic-algorithms)

### <a name="ca5351-do-not-use-broken-cryptographic-algorithms"></a>CA5351: Nepoužívejte poškozené kryptografické algoritmy

Díky tomu výpočetně přerušení tento algoritmus útoku existuje. To útočníkům umožňuje rozdělit kryptografických záruky, které je navržené pro poskytování. V závislosti na typu a použití tohoto kryptografických algoritmů to můžou útočníkům umožnit, aby číst enciphered zprávy, manipulovat s enciphered zprávy, forge digitální podpisy, manipulovat s hodnotu hash obsahu nebo jinak ohrozit zabezpečení jakékoli cryptosystem na základě na tento algoritmus. Pro šifrování, použijte algoritmus AES (AES-256, AES-192 a AES-128 jsou přijatelná) s délkou klíče větší než nebo rovna hodnotě 128 bitů. Pro vytvoření hodnoty hash, pomocí funkce algoritmu hash řady SHA-2, jako je například SHA512, SHA384 nebo SHA256. Pro digitální podpisy použijte RSA s délkou klíče větší než nebo rovna hodnotě 2 048 bitů nebo ECDSA s délkou klíče větší než nebo rovna 256 bitů.

**Kategorie:** Zabezpečení

**Závažnost:** Upozornění

Další informace: [CA5351: Nepoužívejte poškozené kryptografické algoritmy](/visualstudio/code-quality/ca5351-do-not-use-broken-cryptographic-algorithms)

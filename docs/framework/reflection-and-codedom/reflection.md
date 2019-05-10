---
title: Reflexe v rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], reflection
- EventInfo class, reflection
- common language runtime, reflection
- FieldInfo class, reflection
- ParameterInfo class, reflection
- ConstructorInfo class, reflection
- Assembly class, reflection
- value types, reflection
- reflection, about reflection
- modules, reflection
- runtime, reflection
- Module class, reflection
- MethodInfo class, reflection
- PropertyInfo class, reflection
- type browsers
- reflection
- discovering type information at run time
- type system, reflection
ms.assetid: d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cd9fb96f69da977efd2eee6f740cc93ad58e6ea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591483"
---
# <a name="reflection-in-the-net-framework"></a>Reflexe v rozhraní .NET Framework
Třídy v <xref:System.Reflection> obor názvů, společně s <xref:System.Type?displayProperty=nameWithType>, vám umožní získat informace o načtených [sestavení](../app-domains/assemblies-in-the-common-language-runtime.md) a typy definované v nich, jako například [třídy](../../standard/base-types/common-type-system.md#classes), [rozhraní](../../standard/base-types/common-type-system.md#interfaces), a [typů hodnot](../../csharp/language-reference/keywords/value-types.md). Reflexe můžete také použít k vytvoření instance typu v době běhu a k vyvolání a přistupovat k nim. Témata týkající se konkrétní aspekty reflexe, naleznete v tématu [související témata](#related_topics) na konci tohoto přehledu.
  
 [Společného jazykového modulu runtime](../../../docs/standard/clr.md) zavaděč spravuje [aplikačních doménách](../../../docs/framework/app-domains/application-domains.md), které tvoří definované hranice kolem objektů, které mají stejné oboru aplikace. Tato správa zahrnuje načítání každé sestavení do domény příslušné aplikace a řízení rozložení paměti hierarchie typů v rámci každého sestavení.  
  
 [Sestavení](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) obsahovat moduly, moduly obsahují typy a typy obsahovat členy. Reflexe obsahuje objekty, které zapouzdřují sestavení, modulů a typů. Vám pomůže odrazu dynamicky vytvořit instanci typu, navázat na existující objekt nebo získat typ z existujícího objektu. Potom můžete volat metody typu nebo přístup k vlastnostem a polím. Typické použití reflexe patří:  
  
- Použití <xref:System.Reflection.Assembly> definovat a načítat sestavení, načtení modulů, které jsou uvedeny v manifestu sestavení a vyhledejte typu v tomto sestavení a vytvořte její instanci.  
  
- Použití <xref:System.Reflection.Module> zjistit informace, jako jsou sestavení, který obsahuje třídy v modulu a modulu. Můžete také získat všechny globální metody nebo jiných konkrétní, neglobální metody definované v modulu.  
  
- Použití <xref:System.Reflection.ConstructorInfo> zjistit informace, jako je název, parametry, modifikátorů přístupu (například `public` nebo `private`) a podrobnosti implementace (například `abstract` nebo `virtual`) konstruktoru. Použití <xref:System.Type.GetConstructors%2A> nebo <xref:System.Type.GetConstructor%2A> metodu <xref:System.Type> k vyvolání konkrétního konstruktoru.  
  
- Použití <xref:System.Reflection.MethodInfo> zjistit informace, jako je název, návratový typ parametrů, modifikátorů přístupu (například `public` nebo `private`) a podrobnosti implementace (například `abstract` nebo `virtual`) metody. Použití <xref:System.Type.GetMethods%2A> nebo <xref:System.Type.GetMethod%2A> metodu <xref:System.Type> volání konkrétní metody.  
  
- Použití <xref:System.Reflection.FieldInfo> modifikátorů přístupu ke zjišťování informací, například jména, (například `public` nebo `private`) a podrobnosti implementace (například `static`) pole a k získání nebo nastavení hodnoty polí.  
  
- Použití <xref:System.Reflection.EventInfo> zjistit informace, jako je název, datový typ obslužné rutiny události, vlastní atributy deklarující typ a reflektovaných typ události a chcete přidat nebo odebrat obslužných rutin událostí.  
  
- Použití <xref:System.Reflection.PropertyInfo> ke zjišťování informací, například jména, projeví datový typ deklarující typ, typ a stav jen pro čtení nebo zápis vlastnosti a k získání nebo nastavení hodnot vlastností.  
  
- Použití <xref:System.Reflection.ParameterInfo> zjistit informace, jako je název parametru, datový typ, zda je parametr vstupní nebo výstupní parametr a umístění parametru v podpisu metody.  
  
- Použití <xref:System.Reflection.CustomAttributeData> zjistí informace o uživatelských atributů, které při práci v rámci domény aplikace pouze pro reflexi. <xref:System.Reflection.CustomAttributeData> umožňuje zkoumat atributy bez vytvoření instance z nich.  
  
 Třídy <xref:System.Reflection.Emit> obor názvů poskytují specializovaná forma reflexe, který vám umožní sestavovat typy v době běhu.  
  
 Reflexe je také možné vytvářet aplikace s názvem typu prohlížeče, které umožňují uživatelům vybrat typy a zobrazte si informace o těchto typech.  
  
 Existují jiné účely reflexe. Kompilátory jazyků, jako jsou JScript pomocí reflexe k vytvoření tabulky symbolů. Třídy v <xref:System.Runtime.Serialization> oboru názvů pomocí reflexe pro přístup k datům a k určení pole, která chcete zachovat. Třídy v <xref:System.Runtime.Remoting> oboru názvů pomocí reflexe nepřímo prostřednictvím serializace.  
  
## <a name="runtime-types-in-reflection"></a>Typy runtime v reflexi  
 Reflexe poskytuje třídy, jako například <xref:System.Type> a <xref:System.Reflection.MethodInfo>, představující typy, členy, parametry a další entity kódu. Při použití reflexe nechcete pracovat přímo s těchto tříd, z nichž většina ale abstraktní (`MustInherit` v jazyce Visual Basic). Místo toho můžete pracovat se typy poskytované modulem common language runtime (CLR).  
  
 Například při použití jazyka C# `typeof` – operátor (`GetType` v jazyce Visual Basic) k získání <xref:System.Type> objekt, objekt je ve skutečnosti `RuntimeType`. `RuntimeType` je odvozen od <xref:System.Type>a poskytuje implementaci abstraktní metody.  
  
 Tyto třídy modulu runtime jsou `internal` (`Friend` v jazyce Visual Basic). Jejich nejsou zdokumentován samostatně z jejich základních tříd, protože jejich chování je popsán v dokumentaci k základní třídě.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|Popisuje <xref:System.Type> třídy a poskytuje příklady kódu, které ukazují, jak používat <xref:System.Type> s několika třídami reflexe k získání informací o konstruktory, metody, pole, vlastnosti a události.|  
|[Reflexe a obecné typy](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)|Vysvětluje, jak reflexe zpracovává parametry typu a argumenty typu obecné typy a obecné metody.|  
|[Důležité informace o zabezpečení pro reflexi](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)|Popisuje pravidla, které určují, do jaké míry reflexe umožňuje zjišťovat typy informací a přístup k typu.|  
|[Dynamické načtení a použití typů](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md)|Popisuje rozhraní reflexe vlastní vazby, který podporuje pozdní vazbu.|  
|[Postupy: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Popisuje kontext načítání pouze pro reflexi. Ukazuje, jak načíst sestavení, testování kontextu a jak prozkoumat atributy použité u sestavení do kontextu pouze pro reflexi.|  
|[Přístup k vlastním atributům](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)|Ukazuje použití reflexe pro dotaz atribut existenci a hodnoty.|  
|[Určení úplných názvů typů](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)|Popisuje formát plně kvalifikované názvy typů z hlediska Backus-Naur – formulář (BNF) a syntaxi pro zadávání speciálních znaků, názvy sestavení, ukazatele, reference a pole.|  
|[Postupy: Připojení delegáta pomocí reflexe](../../../docs/framework/reflection-and-codedom/how-to-hook-up-a-delegate-using-reflection.md)|Vysvětluje, jak vytvořit delegáta pro metodu a zapojit delegát až událost. Vysvětluje, jak vytvořit metodu zpracování událostí v době běhu pomocí <xref:System.Reflection.Emit.DynamicMethod>.|  
|[Generování dynamických metod a sestavení](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Vysvětluje, jak ke generování dynamických sestavení a dynamické metody.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Type?displayProperty=nameWithType>  
  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  

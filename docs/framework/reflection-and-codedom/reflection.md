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
ms.openlocfilehash: c8d34c5386d0ede578fec097279e9de135f4b6cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940033"
---
# <a name="reflection-in-the-net-framework"></a>Reflexe v rozhraní .NET Framework
<xref:System.Reflection> Třídy v oboru názvů spolu s <xref:System.Type?displayProperty=nameWithType>umožňují získat informace o načtených [sestaveních](../app-domains/assemblies-in-the-common-language-runtime.md) a typech, které jsou v nich definovány, jako jsou [třídy](../../standard/base-types/common-type-system.md#classes), [rozhraní](../../standard/base-types/common-type-system.md#interfaces)a [typy hodnot](../../csharp/language-reference/keywords/value-types.md). Reflexe můžete také použít k vytvoření instancí typu za běhu a k jejich vyvolání a přístup k nim. Témata týkající se konkrétních aspektů reflexe najdete v části [Příbuzná témata](#related_topics) na konci tohoto přehledu.
  
 Modul [CLR (Common Language Runtime)](../../standard/clr.md) spravuje [aplikační domény](../../../docs/framework/app-domains/application-domains.md), které tvoří hranice kolem objektů, které mají stejný obor aplikace. Tato Správa zahrnuje načtení každého sestavení do příslušné aplikační domény a řízení rozložení paměti hierarchie typů v rámci každého sestavení.  
  
 [Sestavení](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) obsahují moduly, moduly obsahují typy a typy obsahují členy. Reflexe poskytuje objekty, které zapouzdřují sestavení, moduly a typy. Můžete použít reflexi k dynamickému vytvoření instance typu, svázání typu s existujícím objektem nebo získání typu z existujícího objektu. Pak můžete vyvolat metody typu nebo získat přístup k jeho polím a vlastnostem. Mezi Typická použití reflexe patří následující:  
  
- Použijte <xref:System.Reflection.Assembly> k definování a načtení sestavení, načtení modulů, které jsou uvedeny v manifestu sestavení a vyhledejte typ z tohoto sestavení a vytvořte jeho instanci.  
  
- Slouží <xref:System.Reflection.Module> ke zjištění informací, jako je sestavení, které obsahuje modul a třídy v modulu. Můžete také získat všechny globální metody nebo jiné specifické neglobální metody definované v modulu.  
  
- Slouží <xref:System.Reflection.ConstructorInfo> ke zjištění informací, jako je název, parametry, modifikátory přístupu ( `public` například nebo `private` `abstract` ), a podrobnosti implementace (například nebo `virtual`) konstruktoru. Použijte metodu <xref:System.Type.GetConstructors%2A> nebo <xref:System.Type.GetConstructor%2A> metody<xref:System.Type> k vyvolání konkrétního konstruktoru.  
  
- Slouží <xref:System.Reflection.MethodInfo> ke zjištění informací, jako je název, návratový typ, parametry, modifikátory přístupu ( `public` například nebo `private` `abstract` ) a podrobnosti implementace (například nebo `virtual`) metody. Použijte metodu <xref:System.Type.GetMethods%2A> nebo <xref:System.Type.GetMethod%2A> metody<xref:System.Type> k vyvolání konkrétní metody.  
  
- Slouží <xref:System.Reflection.FieldInfo> ke zjištění informací, jako je název, modifikátory přístupu ( `public` například nebo `private`) a podrobné informace o implementaci (například `static`) a k získání nebo nastavení hodnot polí.  
  
- Slouží <xref:System.Reflection.EventInfo> ke zjištění informací, jako je název, datový typ obslužné rutiny události, vlastní atributy, deklarující typ a reflektující se typ události a přidání nebo odebrání obslužných rutin událostí.  
  
- Slouží <xref:System.Reflection.PropertyInfo> ke zjištění informací, jako je název, datový typ, deklarující typ, reflektující typ a stav jen pro čtení nebo zapisovatelný stav vlastnosti a získání nebo nastavení hodnot vlastností.  
  
- Slouží <xref:System.Reflection.ParameterInfo> ke zjištění informací, jako je název parametru, datový typ, bez ohledu na to, zda je parametr vstupní nebo výstupní parametr a pozice parametru v signatuře metody.  
  
- Slouží <xref:System.Reflection.CustomAttributeData> ke zjištění informací o vlastních atributech při práci v kontextu pouze pro reflexi domény aplikace. <xref:System.Reflection.CustomAttributeData>slouží k prohlédnutí atributů bez vytváření instancí.  
  
 Třídy <xref:System.Reflection.Emit> oboru názvů poskytují specializované formy reflexe, které umožňují vytvářet typy v době běhu.  
  
 Reflexi lze také použít k vytváření aplikací nazývaných prohlížeč typu, které umožňují uživatelům vybrat typy a poté zobrazit informace o těchto typech.  
  
 Existují i jiné způsoby, jak reflexe. Kompilátory pro jazyky, jako je JScript, používají reflexi k vytváření tabulek symbolů. Třídy v <xref:System.Runtime.Serialization> oboru názvů používají reflexi pro přístup k datům a určují, která pole se mají zachovat. Třídy v <xref:System.Runtime.Remoting> oboru názvů používají reflexi nepřímo prostřednictvím serializace.  
  
## <a name="runtime-types-in-reflection"></a>Typy runtime v reflexi  
 Reflexe poskytuje třídy, <xref:System.Type> jako <xref:System.Reflection.MethodInfo>jsou a, k reprezentaci typů, členů, parametrů a dalších entit kódu. Pokud však použijete reflexi, nepracujete přímo s těmito třídami, přičemž většina z`MustInherit` nich je abstraktní (v Visual Basic). Místo toho pracujete s typy poskytnutými modulem CLR (Common Language Runtime).  
  
 Například C# `typeof` při použití operátoru (`GetType` v Visual Basic) k získání <xref:System.Type> objektu je objekt skutečně `RuntimeType`. `RuntimeType`je odvozen z <xref:System.Type>a poskytuje implementace všech abstraktních metod.  
  
 Tyto běhové třídy `internal` jsou`Friend` (v Visual Basic). Nejsou dokumentovány odděleně od jejich základních tříd, protože jejich chování je popsáno v dokumentaci základní třídy.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|Popisuje třídu a poskytuje příklady kódu, které ilustrují, jak použít <xref:System.Type> s několika třídami Reflection k získání informací o konstruktorech, metodách, polích, vlastnostech a událostech. <xref:System.Type>|  
|[Reflexe a obecné typy](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)|Vysvětluje, jak reflexe zpracovává parametry typu a argumenty typů obecných typů a obecných metod.|  
|[Důležité informace o zabezpečení pro reflexi](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)|Popisuje pravidla, která určují, jaké reflexe úrovně lze použít ke zjištění informací o typu a přístupových typů.|  
|[Dynamické načtení a použití typů](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md)|Popisuje rozhraní vlastní vazby odrazu, které podporuje pozdní vazbu.|  
|[Postupy: Načíst sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Popisuje kontext načtení pouze pro reflexi. Ukazuje, jak načíst sestavení, jak testovat kontext a jak kontrolovat atributy použité pro sestavení v kontextu pouze pro reflexi.|  
|[Přístup k vlastním atributům](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)|Ukazuje použití reflexe pro dotaz na existenci a hodnoty atributu.|  
|[Určení úplných názvů typů](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)|Popisuje formát plně kvalifikovaných názvů typů v souvislosti s formulářem Backus-Naur (BNF) a syntaxí nutnou pro zadání speciálních znaků, názvů sestavení, ukazatelů, odkazů a polí.|  
|[Postupy: Připojit delegáta pomocí reflexe](../../../docs/framework/reflection-and-codedom/how-to-hook-up-a-delegate-using-reflection.md)|Vysvětluje, jak vytvořit delegáta pro metodu a zapojit delegáta do události. Vysvětluje, jak vytvořit metodu zpracování událostí v době běhu pomocí <xref:System.Reflection.Emit.DynamicMethod>.|  
|[Generování dynamických metod a sestavení](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Vysvětluje, jak generovat dynamická sestavení a dynamické metody.|  
  
## <a name="reference"></a>Reference  
 <xref:System.Type?displayProperty=nameWithType>  
  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  

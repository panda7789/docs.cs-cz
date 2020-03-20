---
title: Reflexe v rozhraní .NET
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET], reflection
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
ms.openlocfilehash: 90d9cf4c473d73d1eeeb5f2a1098f8626c20359f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180479"
---
# <a name="reflection-in-net"></a>Reflexe v rozhraní .NET

Třídy v <xref:System.Reflection> oboru názvů <xref:System.Type?displayProperty=nameWithType>spolu s rozhraním umožňují získat informace o načtených sestaveních a typech v nich [definovaných,](../../standard/assembly/index.md) jako jsou [třídy](../../standard/base-types/common-type-system.md#classes), [rozhraní](../../standard/base-types/common-type-system.md#interfaces)a typy hodnot (tj. [struktury](../../standard/base-types/common-type-system.md#structures) a [výčty).](../../standard/base-types/common-type-system.md#enumerations) Reflexe můžete také použít k vytvoření instance typu za běhu a k vyvolání a přístupu k nim. Témata týkající se konkrétních aspektů reflexe naleznete v [tématu Příbuzná témata](#related_topics) na konci tohoto přehledu.
  
Zavaděč [běžného běhu jazyka](../../standard/clr.md) spravuje [aplikační domény](../app-domains/application-domains.md), které představují definované hranice kolem objektů, které mají stejný rozsah aplikace. Tato správa zahrnuje načítání každého sestavení do příslušné domény aplikace a řízení rozložení paměti hierarchie typů v rámci každého sestavení.  
  
[Sestavení](../app-domains/index.md) obsahují moduly, moduly obsahují typy a typy obsahují členy. Reflexe poskytuje objekty, které zapouzdřují sestavení, moduly a typy. Odraz můžete použít k dynamickému vytvoření instance typu, svázání typu s existujícím objektem nebo získání typu z existujícího objektu. Potom můžete vyvolat metody typu nebo přístup k jeho polím a vlastnostem. Typické použití reflexe patří následující:  
  
- Slouží <xref:System.Reflection.Assembly> k definování a načtení sestavení, zatížení modulů, které jsou uvedeny v manifestu sestavení a vyhledejte typ z tohoto sestavení a vytvořte jeho instanci.  
  
- Slouží <xref:System.Reflection.Module> ke zjištění informací, jako je například sestavení, které obsahuje modul a třídy v modulu. Můžete také získat všechny globální metody nebo jiné specifické, neglobální metody definované v modulu.  
  
- Slouží <xref:System.Reflection.ConstructorInfo> ke zjišťování informací, jako je název, parametry, `public` `private`modifikátory přístupu `abstract` `virtual`(například nebo ) a podrobnosti implementace (například nebo ) konstruktoru. Použijte <xref:System.Type.GetConstructors%2A> metodu <xref:System.Type.GetConstructor%2A> nebo <xref:System.Type> k vyvolání konkrétního konstruktoru.  
  
- Slouží <xref:System.Reflection.MethodInfo> ke zjišťování informací, jako je název, návratový typ, `public` parametry, modifikátory přístupu (například nebo `private`) a podrobnosti implementace (například `abstract` nebo `virtual`) metody. Použijte <xref:System.Type.GetMethods%2A> metodu <xref:System.Type.GetMethod%2A> nebo <xref:System.Type> k vyvolání určité metody.  
  
- Slouží <xref:System.Reflection.FieldInfo> ke zjišťování informací, jako je název, `public` modifikátory přístupu (například nebo) `private`a podrobnosti implementace (například) `static`pole, a k získání nebo nastavení hodnot polí.  
  
- Slouží <xref:System.Reflection.EventInfo> ke zjišťování informací, jako je název, datový typ obslužné rutiny událostí, vlastní atributy, deklarující typ a odražený typ události, a k přidání nebo odebrání obslužných rutin událostí.  
  
- Slouží <xref:System.Reflection.PropertyInfo> ke zjišťování informací, jako je název, datový typ, deklarování typu, odraženého typu a stavu vlastnosti jen pro čtení nebo zápis, a k získání nebo nastavení hodnot vlastností.  
  
- Slouží <xref:System.Reflection.ParameterInfo> ke zjištění informací, jako je název parametru, datový typ, zda je parametr vstupní mandatorní nebo výstupní parametr a umístění parametru v podpisu metody.  
  
- Slouží <xref:System.Reflection.CustomAttributeData> ke zjišťování informací o vlastních atributech při práci v kontextu domény aplikace pouze reflexe. <xref:System.Reflection.CustomAttributeData>umožňuje zkoumat atributy bez vytváření jejich instancí.  
  
Třídy oboru <xref:System.Reflection.Emit> názvů poskytují specializovanou formu reflexe, která umožňuje vytvářet typy za běhu.  
  
Reflexe lze také použít k vytvoření aplikací nazývaných prohlížeče typů, které uživatelům umožňují vybrat typy a poté zobrazit informace o těchto typech.  
  
Existují i jiné využití pro reflexi. Kompilátory pro jazyky, jako je JScript, používají reflexe k vytváření tabulek symbolů. Třídy v <xref:System.Runtime.Serialization> oboru názvů používají reflexe pro přístup k datům a k určení, která pole mají být zachována. Třídy v <xref:System.Runtime.Remoting> oboru názvů používají reflexe nepřímo prostřednictvím serializace.  
  
## <a name="runtime-types-in-reflection"></a>Typy runtime v reflexi  
Reflexe poskytuje třídy, jako je například <xref:System.Type> a <xref:System.Reflection.MethodInfo>, představují typy, členy, parametry a další entity kódu. Však při použití reflexe, nepracujete přímo s těmito třídami, z nichž většina jsou abstraktní (v`MustInherit` jazyce Visual Basic). Místo toho pracujete s typy poskytovanými běžným jazykem runtime (CLR).  
  
Například při použití c# `typeof` operátor`GetType` ( v jazyce <xref:System.Type> Visual Basic) k `RuntimeType`získání objektu, objekt je opravdu . `RuntimeType`odvozuje <xref:System.Type> a poskytuje implementace všech abstraktních metod.  
  
Tyto runtime `internal` třídy jsou (`Friend` v jazyce Visual Basic). Nejsou dokumentovány odděleně od svých základních tříd, protože jejich chování je popsáno v dokumentaci základní třídy.  
  
<a name="related_topics"></a>

## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Zobrazení informací o typu](viewing-type-information.md)|Popisuje třídu <xref:System.Type> a poskytuje příklady kódu, <xref:System.Type> které ilustrují použití s několika třídami odrazu k získání informací o konstruktorech, metodách, polích, vlastnostech a událostech.|  
|[Reflexe a obecné typy](reflection-and-generic-types.md)|Vysvětluje, jak reflexe zpracovává parametry typu a argumenty typu obecných typů a obecných metod.|  
|[Důležité informace o zabezpečení pro reflexi](security-considerations-for-reflection.md)|Popisuje pravidla, která určují, do jaké míry lze odraz použít ke zjištění informací o typu a typů přístupu.|  
|[Dynamické načtení a použití typů](dynamically-loading-and-using-types.md)|Popisuje reflexe vlastní vazby rozhraní, které podporuje pozdní vazby.|  
|[Postupy: Načtení sestavení do kontextu pouze pro reflexi](how-to-load-assemblies-into-the-reflection-only-context.md)|Popisuje kontext načítání pouze reflexe. Ukazuje, jak načíst sestavení, jak otestovat kontext a jak prozkoumat atributy použité pro sestavení v kontextu pouze reflexe.|  
|[Přístup k vlastním atributům](accessing-custom-attributes.md)|Ukazuje použití reflexe k existenci atributu dotazu a hodnoty.|  
|[Určení úplných názvů typů](specifying-fully-qualified-type-names.md)|Popisuje formát plně kvalifikovaných názvů typů z hlediska formuláře Backus-Naur (BNF) a syntaxe požadované pro určení speciálních znaků, názvů sestavení, ukazatelů, odkazů a polí.|  
|[Postupy: Připojení delegáta pomocí reflexe](how-to-hook-up-a-delegate-using-reflection.md)|Vysvětluje, jak vytvořit delegáta pro metodu a připojit delegáta k události. Vysvětluje, jak vytvořit metodu zpracování událostí <xref:System.Reflection.Emit.DynamicMethod>za běhu pomocí aplikace .|  
|[Generování dynamických metod a sestavení](emitting-dynamic-methods-and-assemblies.md)|Vysvětluje, jak generovat dynamická sestavení a dynamické metody.|  
  
## <a name="reference"></a>Referenční informace  

<xref:System.Type?displayProperty=nameWithType>  
  
<xref:System.Reflection>  
  
<xref:System.Reflection.Emit>  

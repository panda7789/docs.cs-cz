---
title: Odraz v .NET
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
ms.openlocfilehash: 1768acd65b738af068cf98a8b8340c3179e9b885
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130051"
---
# <a name="reflection-in-net"></a>Odraz v .NET

Třídy v oboru názvů <xref:System.Reflection> společně s <xref:System.Type?displayProperty=nameWithType>umožňují získat informace o načtených [sestaveních](../../standard/assembly/index.md) a typech definovaných v nich, jako jsou [třídy](../../standard/base-types/common-type-system.md#classes), [rozhraní](../../standard/base-types/common-type-system.md#interfaces)a [typy hodnot](../../csharp/language-reference/keywords/value-types.md). Reflexe můžete také použít k vytvoření instancí typu za běhu a k jejich vyvolání a přístup k nim. Témata týkající se konkrétních aspektů reflexe najdete v části [Příbuzná témata](#related_topics) na konci tohoto přehledu.
  
Modul [CLR (Common Language Runtime)](../../standard/clr.md) spravuje [aplikační domény](../app-domains/application-domains.md), které tvoří hranice kolem objektů, které mají stejný obor aplikace. Tato Správa zahrnuje načtení každého sestavení do příslušné aplikační domény a řízení rozložení paměti hierarchie typů v rámci každého sestavení.  
  
[Sestavení](../app-domains/index.md) obsahují moduly, moduly obsahují typy a typy obsahují členy. Reflexe poskytuje objekty, které zapouzdřují sestavení, moduly a typy. Můžete použít reflexi k dynamickému vytvoření instance typu, svázání typu s existujícím objektem nebo získání typu z existujícího objektu. Pak můžete vyvolat metody typu nebo získat přístup k jeho polím a vlastnostem. Mezi Typická použití reflexe patří následující:  
  
- Pomocí <xref:System.Reflection.Assembly> definujte a načtěte sestavení, načtěte moduly, které jsou uvedeny v manifestu sestavení a vyhledejte typ z tohoto sestavení a vytvořte jeho instanci.  
  
- Pomocí <xref:System.Reflection.Module> můžete zjistit informace, jako je například sestavení obsahující modul a třídy v modulu. Můžete také získat všechny globální metody nebo jiné specifické neglobální metody definované v modulu.  
  
- Pomocí <xref:System.Reflection.ConstructorInfo> můžete zjistit informace, jako je název, parametry, modifikátory přístupu (například `public` nebo `private`), a podrobnosti implementace (například `abstract` nebo `virtual`) konstruktoru. K vyvolání konkrétního konstruktoru použijte metodu <xref:System.Type.GetConstructors%2A> nebo <xref:System.Type.GetConstructor%2A> <xref:System.Type>.  
  
- Pomocí <xref:System.Reflection.MethodInfo> můžete zjistit informace, jako je název, návratový typ, parametry, modifikátory přístupu (například `public` nebo `private`), a podrobnosti implementace (například `abstract` nebo `virtual`) metody. K vyvolání konkrétní metody použijte metodu <xref:System.Type.GetMethods%2A> nebo <xref:System.Type.GetMethod%2A> <xref:System.Type>.  
  
- Pomocí <xref:System.Reflection.FieldInfo> můžete zjišťovat informace, jako je název, modifikátory přístupu (například `public` nebo `private`) a podrobnosti implementace (například `static`) pole a získat nebo nastavit hodnoty polí.  
  
- Pomocí <xref:System.Reflection.EventInfo> můžete zjistit informace, jako je název, datový typ obslužné rutiny události, vlastní atributy, deklarující typ a reflektující typ události a přidat nebo odebrat obslužné rutiny událostí.  
  
- Pomocí <xref:System.Reflection.PropertyInfo> můžete zjišťovat informace, jako je název, datový typ, deklarující typ, reflektující typ a stav jen pro čtení nebo zapisovatelný stav vlastnosti, a získat nebo nastavit hodnoty vlastností.  
  
- Pomocí <xref:System.Reflection.ParameterInfo> můžete zjistit informace, jako je název parametru, datový typ, to, zda je parametr vstupní nebo výstupní parametr a pozice parametru v signatuře metody.  
  
- Použijte <xref:System.Reflection.CustomAttributeData> pro zjišťování informací o vlastních atributech při práci v kontextu pouze pro reflexi domény aplikace. <xref:System.Reflection.CustomAttributeData> slouží k prohlédnutí atributů bez vytváření instancí.  
  
Třídy oboru názvů <xref:System.Reflection.Emit> poskytují specializované formy reflexe, které umožňují vytvářet typy v době běhu.  
  
Reflexi lze také použít k vytváření aplikací nazývaných prohlížeč typu, které umožňují uživatelům vybrat typy a poté zobrazit informace o těchto typech.  
  
Existují i jiné způsoby, jak reflexe. Kompilátory pro jazyky, jako je JScript, používají reflexi k vytváření tabulek symbolů. Třídy v oboru názvů <xref:System.Runtime.Serialization> používají reflexi pro přístup k datům a určují, která pole se mají zachovat. Třídy v oboru názvů <xref:System.Runtime.Remoting> používají reflexi nepřímo prostřednictvím serializace.  
  
## <a name="runtime-types-in-reflection"></a>Typy runtime v reflexi  
Reflexe poskytuje třídy, například <xref:System.Type> a <xref:System.Reflection.MethodInfo>, k reprezentaci typů, členů, parametrů a dalších entit kódu. Nicméně při použití reflexe nepracujete přímo s těmito třídami, přičemž většina z nich je abstraktní (`MustInherit` v Visual Basic). Místo toho pracujete s typy poskytnutými modulem CLR (Common Language Runtime).  
  
Například při použití operátoru C# `typeof` (`GetType` v Visual Basic) k získání objektu <xref:System.Type> je objekt skutečně `RuntimeType`. `RuntimeType` je odvozen z <xref:System.Type> a poskytuje implementace všech abstraktních metod.  
  
Tyto běhové třídy jsou `internal` (`Friend` v Visual Basic). Nejsou dokumentovány odděleně od jejich základních tříd, protože jejich chování je popsáno v dokumentaci základní třídy.  
  
<a name="related_topics"></a>   

## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Zobrazení informací o typu](viewing-type-information.md)|Popisuje třídu <xref:System.Type> a poskytuje příklady kódu, které ilustrují použití <xref:System.Type> s několika třídami Reflection k získání informací o konstruktorech, metodách, polích, vlastnostech a událostech.|  
|[Reflexe a obecné typy](reflection-and-generic-types.md)|Vysvětluje, jak reflexe zpracovává parametry typu a argumenty typů obecných typů a obecných metod.|  
|[Důležité informace o zabezpečení pro reflexi](security-considerations-for-reflection.md)|Popisuje pravidla, která určují, jaké reflexe úrovně lze použít ke zjištění informací o typu a přístupových typů.|  
|[Dynamické načtení a použití typů](dynamically-loading-and-using-types.md)|Popisuje rozhraní vlastní vazby odrazu, které podporuje pozdní vazbu.|  
|[Postupy: Načtení sestavení do kontextu pouze pro reflexi](how-to-load-assemblies-into-the-reflection-only-context.md)|Popisuje kontext načtení pouze pro reflexi. Ukazuje, jak načíst sestavení, jak testovat kontext a jak kontrolovat atributy použité pro sestavení v kontextu pouze pro reflexi.|  
|[Přístup k vlastním atributům](accessing-custom-attributes.md)|Ukazuje použití reflexe pro dotaz na existenci a hodnoty atributu.|  
|[Určení úplných názvů typů](specifying-fully-qualified-type-names.md)|Popisuje formát plně kvalifikovaných názvů typů v souvislosti s formulářem Backus-Naur (BNF) a syntaxí nutnou pro zadání speciálních znaků, názvů sestavení, ukazatelů, odkazů a polí.|  
|[Postupy: Připojení delegáta pomocí reflexe](how-to-hook-up-a-delegate-using-reflection.md)|Vysvětluje, jak vytvořit delegáta pro metodu a zapojit delegáta do události. Vysvětluje, jak vytvořit metodu zpracování událostí v době běhu pomocí <xref:System.Reflection.Emit.DynamicMethod>.|  
|[Generování dynamických metod a sestavení](emitting-dynamic-methods-and-assemblies.md)|Vysvětluje, jak generovat dynamická sestavení a dynamické metody.|  
  
## <a name="reference"></a>Odkaz  

<xref:System.Type?displayProperty=nameWithType>  
  
<xref:System.Reflection>  
  
<xref:System.Reflection.Emit>  

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
ms.openlocfilehash: ef4e2918b682d964b7f65eb98d497715d1e4ac57
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399055"
---
# <a name="reflection-in-the-net-framework"></a>Reflexe v rozhraní .NET Framework
Třídy v <xref:System.Reflection> obor názvů, společně s <xref:System.Type?displayProperty=nameWithType>, vám umožní získat informace o načíst [sestavení](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) a typů front definovaných v nich, jako například [třídy](http://msdn.microsoft.com/library/ad7d3561-271e-4546-82fc-e00b059f27a9), [rozhraní](http://msdn.microsoft.com/library/fd9d5975-5363-4bc9-b883-609f887895e5), a [typů hodnot](http://msdn.microsoft.com/library/c9c567f8-8ab1-4d88-834d-00f7d92418de). Reflexe můžete také použít k vytvoření instance typu za běhu a k vyvolání a přistupovat k nim. Témata o konkrétních aspektů reflexe naleznete v tématu [Příbuzná témata](#related_topics) na konci tohoto přehledu.  
  
 [Modul common language runtime](../../../docs/standard/clr.md) spravuje zavaděč [aplikační domény](../../../docs/framework/app-domains/application-domains.md), které tvoří definované hranice kolem objekty, které mají stejný obor aplikace. Tato správa zahrnuje načítání každé sestavení do domény příslušné aplikace a řízení rozložení paměti hierarchii typů v rámci každé sestavení.  
  
 [Sestavení](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) obsahovat moduly, moduly obsahují typy a typy obsahovat členy. Reflexe poskytuje objekty, které zapouzdřit sestavení, moduly a typy. Reflexe můžete dynamicky vytvořit instanci typu, typ vazby s existujícím objektem nebo získat typ z existujícího objektu. Potom můžete volat metody tohoto typu nebo přístup k jeho polí a vlastností. Typické použití reflexe zahrnují následující:  
  
-   Použití <xref:System.Reflection.Assembly> definovat a načtení sestavení, načíst moduly, které jsou uvedené v manifestu sestavení a vyhledejte typu z tohoto sestavení a vytvořit její instanci.  
  
-   Použití <xref:System.Reflection.Module> ke zjištění informace, jako je sestavení, které obsahuje modul a třídy v modulu. Můžete také získat všechny globální metody nebo jiné metody konkrétní, neglobální definovaná v modulu.  
  
-   Použití <xref:System.Reflection.ConstructorInfo> ke zjištění informace, jako je název, parametry, přístup k modifikátory (například `public` nebo `private`) a podrobnosti implementace (jako `abstract` nebo `virtual`) konstruktoru. Použití <xref:System.Type.GetConstructors%2A> nebo <xref:System.Type.GetConstructor%2A> metodu <xref:System.Type> k vyvolání konkrétní konstruktor.  
  
-   Použití <xref:System.Reflection.MethodInfo> Chcete-li zjistit informace, jako je název, typ, parametry, modifikátory přístupu (například `public` nebo `private`) a podrobnosti implementace (například `abstract` nebo `virtual`) metody. Použití <xref:System.Type.GetMethods%2A> nebo <xref:System.Type.GetMethod%2A> metodu <xref:System.Type> k vyvolání konkrétní metody.  
  
-   Použití <xref:System.Reflection.FieldInfo> Pokud chcete zjistit informace, jako je název, přístup k modifikátory (například `public` nebo `private`) a podrobnosti implementace (například `static`) pole a k získání nebo nastavení hodnoty polí.  
  
-   Použití <xref:System.Reflection.EventInfo> ke zjištění informace, jako je název, datový typ obslužné rutiny události, vlastní atributy, deklarující typ a reflektované typ události a chcete přidat nebo odebrat obslužné rutiny událostí.  
  
-   Použití <xref:System.Reflection.PropertyInfo> Pokud chcete zjistit informace, jako je název, datový typ deklarace typu, projeví typ a stav jen pro čtení nebo zápis vlastnosti a k získání nebo nastavení hodnoty vlastnosti.  
  
-   Použití <xref:System.Reflection.ParameterInfo> Pokud chcete zjistit informace, jako je název parametru, datový typ, zda je parametr vstupní nebo výstupní parametr a pozice parametr v podpis metody.  
  
-   Použití <xref:System.Reflection.CustomAttributeData> chcete zjistit informace o vlastních atributů, když pracujete v kontextu pouze pro reflexi domény aplikace. <xref:System.Reflection.CustomAttributeData> Umožňuje zkontrolovat atributy bez vytváření instancí z nich.  
  
 Třídy <xref:System.Reflection.Emit> oboru názvů zadejte specializovaná forma reflexe, který vám umožní sestavovat typy za běhu.  
  
 Reflexe lze také vytvářet aplikace volá typu prohlížeče, které umožňují uživatelům vybrat typy a zobrazte si informace o těchto typech.  
  
 Existují nějaká jiná použití pro reflexi. Kompilátory pro jazyky, jako je například JScript pomocí reflexe k vytvoření tabulky symbolů. Třídy v <xref:System.Runtime.Serialization> oboru názvů pomocí reflexe pro přístup k datům a k určení pole, která chcete zachovat. Třídy v <xref:System.Runtime.Remoting> oboru názvů pomocí reflexe nepřímo prostřednictvím serializace.  
  
## <a name="runtime-types-in-reflection"></a>Typy runtime v reflexi  
 Reflexe poskytuje třídy, jako například <xref:System.Type> a <xref:System.Reflection.MethodInfo>, představují typy, členy, parametry a dalšími subjekty, kód. Ale pokud používáte reflexe nemáte pracovat přímo s tyto třídy, většina z nich abstraktní (`MustInherit` v jazyce Visual Basic). Místo toho můžete pracovat s typy poskytované common language runtime (CLR).  
  
 Například při použití jazyka C# `typeof` – operátor (`GetType` v jazyce Visual Basic) k získání <xref:System.Type> objektu, objekt je ve skutečnosti `RuntimeType`. `RuntimeType` odvozená z <xref:System.Type>a poskytuje implementaci abstraktní metody.  
  
 Jsou tyto třídy runtime `internal` (`Friend` v jazyce Visual Basic). Jejich nejsou popsané samostatně z jeho základních tříd, protože jejich chování je popsán v dokumentaci základní třídy.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Zobrazení informací o typu](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|Popisuje <xref:System.Type> třídy a poskytuje příklady kódu, které ukazují, jak používat <xref:System.Type> s několik tříd reflexe ke získání informací o konstruktory, metody, pole, vlastnosti a události.|  
|[Reflexe a obecné typy](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)|Vysvětluje, jak reflexe zpracovává typ parametry a argumenty typu obecné typy a obecné metody.|  
|[Důležité informace o zabezpečení pro reflexi](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)|Popisuje pravidla, která určují, do jaké míry reflexe lze zjistit typ typy informací a přístup.|  
|[Dynamické načtení a použití typů](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md)|Popisuje rozhraní reflexe vlastní vazby, které podporuje pozdní vazbu.|  
|[Postupy: Načtení sestavení do kontextu pouze pro reflexi](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Popisuje kontext načítání pouze pro reflexi. Ukazuje, jak načíst sestavení, jak otestovat kontextu a jak prozkoumat atributy použité k sestavení v kontextu pouze pro reflexi.|  
|[Přístup k vlastním atributům](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)|Ukazuje, jak pomocí reflexe do atribut existence dotazu a hodnoty.|  
|[Určení úplných názvů typů](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)|Popisuje formát úplné názvy typů z hlediska Backus-Naur formuláře (BNF) a syntaxi pro určení speciální znaky, názvy sestavení, ukazatelů, odkazy a polí.|  
|[Postupy: Připojení delegáta pomocí reflexe](../../../docs/framework/reflection-and-codedom/how-to-hook-up-a-delegate-using-reflection.md)|Vysvětluje, jak vytvořit delegáta pro metodu a propojte delegát až událost. Vysvětluje, jak vytvořit metodu zpracování událostí v době běhu pomocí <xref:System.Reflection.Emit.DynamicMethod>.|  
|[Generování dynamických metod a sestavení](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Vysvětluje, jak pro generování dynamických sestavení a dynamických metod.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Type?displayProperty=nameWithType>  
  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  

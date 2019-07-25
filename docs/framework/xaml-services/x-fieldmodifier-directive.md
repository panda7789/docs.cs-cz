---
title: x:FieldModifier – direktiva
ms.date: 03/30/2017
helpviewer_keywords:
- FieldModifier attribute in XAML [XAML Services]
- x:FieldModifier attribute [XAML Services]
- XAML [XAML Services], x:FieldModifier attribute
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
ms.openlocfilehash: 646ad1ca99d83f9fb2994f3c394eca27a60c0eac
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484725"
---
# <a name="xfieldmodifier-directive"></a>x:FieldModifier – direktiva
Upraví chování kompilace XAML tak, aby pole pro pojmenované odkazy byla definována <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> s přístupem namísto <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> výchozího chování.  
  
## <a name="xaml-attribute-usage"></a>Použití atributu XAML  
  
```xaml  
<object x:FieldModifier="Public".../>  
```  
  
## <a name="xaml-values"></a>Hodnoty XAML  
  
|||  
|-|-|  
|*Public*|Přesný řetězec, který předáte, <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> se <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> liší v závislosti na použitém programovacím jazyce s kódem na pozadí. Viz poznámky.|  
  
## <a name="dependencies"></a>Závislosti  
 Pokud výroba XAML používá `x:FieldModifier` kdekoli, kořenový prvek této výroby XAML musí deklarovat direktivu [x:Class](x-class-directive.md).  
  
## <a name="remarks"></a>Poznámky  
 `x:FieldModifier`není relevantní pro deklaraci obecné úrovně přístupu třídy nebo jejích členů. Je relevantní pouze pro chování zpracování XAML, je-li zpracován konkrétní objekt XAML, který je součástí výroby XAML, a je objekt, který je potenciálně přístupný v grafu objektu aplikace. Ve výchozím nastavení je odkaz na pole pro takový objekt uchováván jako soukromý, což brání řízení uživatelům v přímém upravování grafu objektů. Místo toho se očekává, že příjemci ovládacího prvku budou upravovat objekt grafu pomocí standardních vzorů, které jsou povoleny programovacími modely, jako je získání kořenového prvku rozložení, kolekce podřízených elementů, vyhrazených veřejných vlastností a tak dále.  
  
 Hodnota `x:FieldModifier` atributu se liší podle programovacího jazyka a jeho účelem se může v konkrétních rozhraních lišit. Řetězec, který se má použít, závisí na tom, <xref:System.CodeDom.Compiler.CodeDomProvider> jak jednotlivé jazyky implementují své a konvertory typů, které <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> vrátí <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>, aby definovali význam pro a a zda se u tohoto jazyka rozlišují malá a velká písmena.  
  
- Řetězec C#, který se má předat k určení <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> , `public`je.  
  
- Pro Microsoft Visual Basic .NET je <xref:System.Reflection.TypeAttributes.Public?displayProperty=nameWithType> `Public`řetězec, který se má předat, označovat.  
  
- Pro C++/CLI nejsou aktuálně k dispozici žádné cíle pro XAML; Proto je řetězec, který se má předat, nedefinovaný.  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> Můžete také zadat (`internal` v C# <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType> `NotPublic`VisualBasic) , ale určení je neobvyklé, protože chování je již výchozím nastavením. `Friend`  
  
 <xref:System.Reflection.TypeAttributes.NotPublic?displayProperty=nameWithType>je výchozí chování, protože je zřídka, že kód mimo sestavení, které kompiluje XAML, potřebuje přístup k elementu vytvořenému XAML. Architektura zabezpečení WPF společně s chováním kompilace XAML nebude deklarovat pole, která ukládají instance elementů jako Public, pokud výslovně nenastavíte `x:FieldModifier` , aby povolovala veřejný přístup.  
  
 `x:FieldModifier`je relevantní pouze pro prvky s [direktivou x:Name](x-name-directive.md) , protože tento název se používá pro odkazování pole poté, co je veřejné.  
  
 Ve výchozím nastavení je částečná třída kořenového prvku veřejná; můžete ji však NonPublic pomocí [direktivy x:ClassModifier –](x-classmodifier-directive.md). [Direktiva x:ClassModifier –](x-classmodifier-directive.md) má také vliv na úroveň přístupu instance třídy kořenového elementu. Můžete umístit obojí `x:Name` i `x:FieldModifier` na kořenový prvek, ale to pouze vytvoří veřejnou kopii kořenového prvku s skutečnou úrovní přístupu třídy kořenového elementu, která je stále řízena direktivou [x:ClassModifier –](x-classmodifier-directive.md).  
  
## <a name="see-also"></a>Viz také:

- [XAML a vlastní třídy pro WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [Podkladový kód a kód XAML v subsystému WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md)
- [x:Name – direktiva](x-name-directive.md)
- [Sestavení aplikace WPF (WPF)](../wpf/app-development/building-a-wpf-application-wpf.md)
- [x:ClassModifier – direktiva](x-classmodifier-directive.md)

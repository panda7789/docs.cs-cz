---
title: Schéma nastavení aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "81242826"
---
# <a name="application-settings-schema"></a><span data-ttu-id="5f47c-102">Schéma nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="5f47c-102">Application Settings schema</span></span>

<span data-ttu-id="5f47c-103">Nastavení aplikace umožňuje aplikaci model Windows Forms nebo ASP.NET ukládat a načítat nastavení s rozsahem aplikace a uživatelem.</span><span class="sxs-lookup"><span data-stu-id="5f47c-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="5f47c-104">V tomto kontextu je *nastavením* jakékoli informace, které mohou být specifické pro aplikaci nebo specifické pro aktuálního uživatele – cokoli z databázového připojovacího řetězce až po upřednostňovanou výchozí velikost okna uživatele.</span><span class="sxs-lookup"><span data-stu-id="5f47c-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="5f47c-105">Ve výchozím nastavení používá nastavení aplikace v model Windows Forms aplikace <xref:System.Configuration.LocalFileSettingsProvider> třídu, která používá konfigurační systém .NET k ukládání nastavení v konfiguračním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="5f47c-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="5f47c-106">Další informace o souborech používaných nastavením aplikace najdete v tématu [Architektura nastavení aplikace](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="5f47c-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="5f47c-107">Nastavení aplikace definuje následující prvky jako součást konfiguračních souborů, které používá.</span><span class="sxs-lookup"><span data-stu-id="5f47c-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="5f47c-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="5f47c-108">Element</span></span>                    | <span data-ttu-id="5f47c-109">Description</span><span class="sxs-lookup"><span data-stu-id="5f47c-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | <span data-ttu-id="5f47c-110">Obsahuje všechny **\<setting>** značky, které jsou specifické pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5f47c-110">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| **\<userSettings>**        | <span data-ttu-id="5f47c-111">Obsahuje všechny **\<setting>** značky, které jsou specifické pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="5f47c-111">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| **\<setting>**             | <span data-ttu-id="5f47c-112">Definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="5f47c-112">Defines a setting.</span></span> <span data-ttu-id="5f47c-113">Podřízená položka **\<applicationSettings>** nebo **\<userSettings>** .</span><span class="sxs-lookup"><span data-stu-id="5f47c-113">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| **\<value>**               | <span data-ttu-id="5f47c-114">Definuje hodnotu nastavení.</span><span class="sxs-lookup"><span data-stu-id="5f47c-114">Defines a setting's value.</span></span> <span data-ttu-id="5f47c-115">Podřízená položka **\<setting>** .</span><span class="sxs-lookup"><span data-stu-id="5f47c-115">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="5f47c-116">\<applicationSettings> – element</span><span class="sxs-lookup"><span data-stu-id="5f47c-116">\<applicationSettings> element</span></span>

<span data-ttu-id="5f47c-117">Tento element obsahuje všechny **\<setting>** značky, které jsou specifické pro instanci aplikace v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="5f47c-117">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="5f47c-118">Nedefinuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="5f47c-118">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="5f47c-119">\<userSettings> – element</span><span class="sxs-lookup"><span data-stu-id="5f47c-119">\<userSettings> element</span></span>

<span data-ttu-id="5f47c-120">Tento prvek obsahuje všechny **\<setting>** značky, které jsou specifické pro uživatele, který aktuálně používá aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5f47c-120">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="5f47c-121">Nedefinuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="5f47c-121">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="5f47c-122">\<setting> – element</span><span class="sxs-lookup"><span data-stu-id="5f47c-122">\<setting> element</span></span>

<span data-ttu-id="5f47c-123">Tento prvek definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="5f47c-123">This element defines a setting.</span></span> <span data-ttu-id="5f47c-124">Má následující atributy.</span><span class="sxs-lookup"><span data-stu-id="5f47c-124">It has the following attributes.</span></span>

| <span data-ttu-id="5f47c-125">Atribut</span><span class="sxs-lookup"><span data-stu-id="5f47c-125">Attribute</span></span>        | <span data-ttu-id="5f47c-126">Popis</span><span class="sxs-lookup"><span data-stu-id="5f47c-126">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="5f47c-127">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="5f47c-127">**name**</span></span>         | <span data-ttu-id="5f47c-128">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="5f47c-128">Required.</span></span> <span data-ttu-id="5f47c-129">Jedinečné ID nastavení</span><span class="sxs-lookup"><span data-stu-id="5f47c-129">The unique ID of the setting.</span></span> <span data-ttu-id="5f47c-130">Nastavení vytvořená pomocí sady Visual Studio se ukládají s názvem `ProjectName.Properties.Settings` .</span><span class="sxs-lookup"><span data-stu-id="5f47c-130">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="5f47c-131">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="5f47c-131">**serializeAs**</span></span> | <span data-ttu-id="5f47c-132">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="5f47c-132">Required.</span></span> <span data-ttu-id="5f47c-133">Formát, který má být použit pro serializaci hodnoty na text.</span><span class="sxs-lookup"><span data-stu-id="5f47c-133">The format to use for serializing the value to text.</span></span> <span data-ttu-id="5f47c-134">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="5f47c-134">Valid values are:</span></span><br><br><span data-ttu-id="5f47c-135">- `string`.</span><span class="sxs-lookup"><span data-stu-id="5f47c-135">- `string`.</span></span> <span data-ttu-id="5f47c-136">Hodnota je serializována jako řetězec pomocí <xref:System.ComponentModel.TypeConverter> .</span><span class="sxs-lookup"><span data-stu-id="5f47c-136">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="5f47c-137">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="5f47c-137">- `xml`.</span></span> <span data-ttu-id="5f47c-138">Hodnota je serializovaná pomocí serializace XML.</span><span class="sxs-lookup"><span data-stu-id="5f47c-138">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="5f47c-139">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="5f47c-139">- `binary`.</span></span> <span data-ttu-id="5f47c-140">Hodnota je serializována jako textový soubor s kódováním pomocí binární serializace.</span><span class="sxs-lookup"><span data-stu-id="5f47c-140">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="5f47c-141">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="5f47c-141">- `custom`.</span></span> <span data-ttu-id="5f47c-142">Poskytovatel nastavení má znalosti tohoto nastavení a serializace a deserializace.</span><span class="sxs-lookup"><span data-stu-id="5f47c-142">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="5f47c-143">\<value> – element</span><span class="sxs-lookup"><span data-stu-id="5f47c-143">\<value> element</span></span>

<span data-ttu-id="5f47c-144">Tento prvek obsahuje hodnotu nastavení.</span><span class="sxs-lookup"><span data-stu-id="5f47c-144">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="5f47c-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f47c-145">Example</span></span>

<span data-ttu-id="5f47c-146">Následující příklad ukazuje soubor nastavení aplikace, který definuje dvě nastavení rozsahu aplikace a dvě nastavení v uživatelském rozsahu:</span><span class="sxs-lookup"><span data-stu-id="5f47c-146">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5f47c-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f47c-147">See also</span></span>

- [<span data-ttu-id="5f47c-148">Přehled nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="5f47c-148">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="5f47c-149">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="5f47c-149">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)

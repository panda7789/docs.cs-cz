---
title: "Schéma nastavení aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
caps.latest.revision: "3"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d93a18b17e0d6b8e413903fb84dc6b427d94f6af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="application-settings-schema"></a><span data-ttu-id="2e940-102">Schéma nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="2e940-102">Application Settings schema</span></span>

<span data-ttu-id="2e940-103">Nastavení aplikace umožňují k aplikaci Windows Forms nebo v technologii ASP.NET pro ukládání a načítání nastavení obor aplikace a nastavení uživatele.</span><span class="sxs-lookup"><span data-stu-id="2e940-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="2e940-104">V tomto kontextu *nastavení* je jakékoliv informace, které může být specifické pro aplikace nebo specifické pro aktuálního uživatele – vše od připojovací řetězec databáze pro uživatele preferovaný výchozí velikost okna.</span><span class="sxs-lookup"><span data-stu-id="2e940-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="2e940-105">Ve výchozím nastavení aplikace v aplikaci Windows Forms používá <xref:System.Configuration.LocalFileSettingsProvider> třídy, která používá konfigurační systém .NET k ukládání nastavení v konfiguračním souboru XML.</span><span class="sxs-lookup"><span data-stu-id="2e940-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="2e940-106">Další informace o souborech používá nastavení aplikace najdete v tématu [architektura nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="2e940-106">For more information about the files used by application settings, see [Application Settings Architecture](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="2e940-107">Nastavení aplikace definuje následující prvky jako součást konfiguračních souborů, které používá.</span><span class="sxs-lookup"><span data-stu-id="2e940-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="2e940-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="2e940-108">Element</span></span>                    | <span data-ttu-id="2e940-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2e940-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="2e940-110">**\<applicationSettings >**</span><span class="sxs-lookup"><span data-stu-id="2e940-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="2e940-111">Obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2e940-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="2e940-112">**\<userSettings >**</span><span class="sxs-lookup"><span data-stu-id="2e940-112">**\<userSettings>**</span></span>        | <span data-ttu-id="2e940-113">Obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="2e940-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="2e940-114">**\<Nastavení >**</span><span class="sxs-lookup"><span data-stu-id="2e940-114">**\<setting>**</span></span>             | <span data-ttu-id="2e940-115">Definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="2e940-115">Defines a setting.</span></span> <span data-ttu-id="2e940-116">Podřízená položka buď  **\<applicationSettings >** nebo  **\<userSettings >**.</span><span class="sxs-lookup"><span data-stu-id="2e940-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="2e940-117">**\<Hodnota >**</span><span class="sxs-lookup"><span data-stu-id="2e940-117">**\<value>**</span></span>               | <span data-ttu-id="2e940-118">Definuje hodnoty nastavení.</span><span class="sxs-lookup"><span data-stu-id="2e940-118">Defines a setting's value.</span></span> <span data-ttu-id="2e940-119">Podřízená položka  **\<Nastavení >**.</span><span class="sxs-lookup"><span data-stu-id="2e940-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="2e940-120">\<applicationSettings > elementu</span><span class="sxs-lookup"><span data-stu-id="2e940-120">\<applicationSettings> element</span></span>

<span data-ttu-id="2e940-121">Tento prvek obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro instance aplikace na klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="2e940-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="2e940-122">Definuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="2e940-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="2e940-123">\<userSettings > elementu</span><span class="sxs-lookup"><span data-stu-id="2e940-123">\<userSettings> element</span></span>

<span data-ttu-id="2e940-124">Tento prvek obsahuje všechny  **\<Nastavení >** značky, které jsou specifické pro uživatele, který je aktuálně používá aplikace.</span><span class="sxs-lookup"><span data-stu-id="2e940-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="2e940-125">Definuje žádné atributy.</span><span class="sxs-lookup"><span data-stu-id="2e940-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="2e940-126">\<Nastavení > elementu</span><span class="sxs-lookup"><span data-stu-id="2e940-126">\<setting> element</span></span>

<span data-ttu-id="2e940-127">Tento element definuje nastavení.</span><span class="sxs-lookup"><span data-stu-id="2e940-127">This element defines a setting.</span></span> <span data-ttu-id="2e940-128">Má následující atributy.</span><span class="sxs-lookup"><span data-stu-id="2e940-128">It has the following attributes.</span></span>

| <span data-ttu-id="2e940-129">Atribut</span><span class="sxs-lookup"><span data-stu-id="2e940-129">Attribute</span></span>        | <span data-ttu-id="2e940-130">Popis</span><span class="sxs-lookup"><span data-stu-id="2e940-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="2e940-131">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="2e940-131">**name**</span></span>         | <span data-ttu-id="2e940-132">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2e940-132">Required.</span></span> <span data-ttu-id="2e940-133">Jedinečné ID nastavení.</span><span class="sxs-lookup"><span data-stu-id="2e940-133">The unique ID of the setting.</span></span> <span data-ttu-id="2e940-134">Nastavení vytvořená pomocí sady Visual Studio se uloží s názvem `ProjectName.Properties.Settings`.</span><span class="sxs-lookup"><span data-stu-id="2e940-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="2e940-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="2e940-135">**serializedAs**</span></span> | <span data-ttu-id="2e940-136">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2e940-136">Required.</span></span> <span data-ttu-id="2e940-137">Formát, který se má použít pro serializaci hodnotu na text.</span><span class="sxs-lookup"><span data-stu-id="2e940-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="2e940-138">Platné hodnoty jsou:</span><span class="sxs-lookup"><span data-stu-id="2e940-138">Valid values are:</span></span><br><br><span data-ttu-id="2e940-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="2e940-139">- `string`.</span></span> <span data-ttu-id="2e940-140">Hodnota je serializován jako řetězec pomocí <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="2e940-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="2e940-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="2e940-141">- `xml`.</span></span> <span data-ttu-id="2e940-142">Hodnota serializován pomocí serializace XML.</span><span class="sxs-lookup"><span data-stu-id="2e940-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="2e940-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="2e940-143">- `binary`.</span></span> <span data-ttu-id="2e940-144">Hodnota je serializováno jako binární kódování textu pomocí binární serializace.</span><span class="sxs-lookup"><span data-stu-id="2e940-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="2e940-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="2e940-145">- `custom`.</span></span> <span data-ttu-id="2e940-146">Poskytovatel nastavení má informace o toto nastavení serializuje a poté serializuje ho.</span><span class="sxs-lookup"><span data-stu-id="2e940-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="2e940-147">\<Hodnota > elementu</span><span class="sxs-lookup"><span data-stu-id="2e940-147">\<value> element</span></span>

<span data-ttu-id="2e940-148">Tento prvek obsahuje hodnotu nastavení.</span><span class="sxs-lookup"><span data-stu-id="2e940-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="2e940-149">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e940-149">Example</span></span>

<span data-ttu-id="2e940-150">Následující příklad ukazuje soubor nastavení aplikace, který definuje dvě nastavení obor aplikace a dvě uživatelských nastavení:</span><span class="sxs-lookup"><span data-stu-id="2e940-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2e940-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e940-151">See also</span></span>

<span data-ttu-id="2e940-152">[Přehled nastavení aplikace](~/docs/framework/winforms/advanced/application-settings-overview.md) </span><span class="sxs-lookup"><span data-stu-id="2e940-152">[Application Settings Overview](~/docs/framework/winforms/advanced/application-settings-overview.md) </span></span>  
[<span data-ttu-id="2e940-153">Architektura nastavení aplikace</span><span class="sxs-lookup"><span data-stu-id="2e940-153">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)

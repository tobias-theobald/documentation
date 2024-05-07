&NewLine;

{{< mermaid class="mermaid_sizing" >}}
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#FFFFFF',
      'primaryTextColor': '#000000',
      'primaryBorderColor': '#0095d5',
      'secondaryColor': '#70d4ff',
      'lineColor': '#0095d5',
      'secondaryTextColor': '#FFFFFF',
      'tertiaryColor': '#0095d5'
    }
  }
}%%

flowchart LR

A["11.0-U7"] -->|update| B["11.2-U8"]
B -->|update| C["11.3-U5"]
C -->|update| D["13.0-U6.1"]
D -->|"(anticipated)"| E["13.3.0"]
{{< /mermaid >}}

<img src="/images/tn-enterprise-logo.png" style="box-shadow: none; max-width: 225px; padding-bottom: 20px; padding-top: 40px;" title="TrueNAS CORE Enterprise" alt="TrueNAS CORE Enterprise">

{{< mermaid class="mermaid_sizing" >}}
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#FFFFFF',
      'primaryTextColor': '#000000',
      'primaryBorderColor': '#0095d5',
      'secondaryColor': '#70d4ff',
      'lineColor': '#0095d5',
      'secondaryTextColor': '#FFFFFF',
      'tertiaryColor': '#0095d5'
    }
  }
}%%

flowchart LR

A["11.0-U7"] -->|update| B["11.2-U8"]
B -->|update| C["11.3-U5"]
C -->|update| D["13.0-U6.1"]
{{< /mermaid >}}